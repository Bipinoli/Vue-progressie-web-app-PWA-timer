<template>
    <div class="screen">
        <div class="time">00:<span class="time-lower">00</span></div>
        <div class="countdown-setup">
            <div class="choice">
                <input type="number" class="min-input" placeholder="minutes" v-model='minutes'>
            </div>
            <div class="row">
                <div class="choice">
                    <input type="number" placeholder="hr" v-model='hours'>
                </div>
                <div class="choice">
                    <input type="number" placeholder="sec" v-model='seconds'>
                </div>
            </div>
        </div>
        <div class="time-control-btn">
            <img src="../assets/resume.svg" alt="resume" @click="toRunning">
        </div>
    </div>
</template>




<script>

export default {
    name: 'CountdownSetup',
    data: function() {
        return timeFactory();
    },
    computed: {
        minutes: {
            get: function() {
                return this.min;
            },
            set: function(val) {
                this.min = val;
            }
        },
        hours: {
            get: function() {
                return this.hr;
            },
            set: function(val) {
                if (val == '') return;
                val = parseInt(val);
                if (val < 0) val = 0;
                if (val > 12) val = 12;
                this.hr = '' + val;
            }
        },
        seconds: {
            get: function() {
                return this.sec;
            },
            set: function(val) {
                this.sec = val;
            }
        }
    },
    methods: {
        toRunning() {
            this.$emit('to-running', {
                'hr': this.hr == '' ?  0 : parseInt(this.hr),
                'min': this.min == '' ? 0 : parseInt(this.min),
                'sec': this.sec == '' ? 0 : parseInt(this.sec)
            });
            Object.assign(this.$data, timeFactory());
        },
    },
}


function timeFactory() {
    return {
            min: '',
            hr: '',
            sec: '',
        };
}

</script>




<style scoped>
    .time {
        font-size: 48px;
        margin-bottom: 1.2em;
    }

    .choice {
        padding: 10px 22px 10px 22px;
        border: 1.1px solid #082D0F;
        border-radius: 15px;
        margin: 10px 5px 10px 5px;
        text-align: center;
        width: fit-content;
    }

    input:focus {
        outline: none;
    }

    input {
        -moz-appearance: textfield;
        text-align: center;
        border: none;
        font-family: 'Montserrat', sans-serif;
        color: #082D0F;
        font-size: 1.2rem;
        width: 5rem;
    }

    input::placeholder {
        font-weight: 300;
        color: #082D0F;
    }

    .min-input {
        width: 13.5rem;
    }

</style>
