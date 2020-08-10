<template>
    <div class="screen">
        <div class="time">{{timeHi}}:<span class="time-lower">{{timeLo}}</span></div>
        <div class="time-label">{{hiLabel}} {{loLabel}}</div>
        <div class="countdown-setup">
            <div class="choice">
                <input type="number" class="min-input" placeholder="minutes" v-model='min'>
            </div>
            <div class="row">
                <div class="choice">
                    <input type="number" placeholder="hr" v-model='hr'>
                </div>
                <div class="choice">
                    <input type="number" placeholder="sec" v-model='sec'>
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
    watch: {
        min: function(val) {
            this.min = bound(val, 0, 59);
            this.adjustDisplayTime();
        },
        hr: function(val) {
            this.hr = bound(val, 0, 12);
            this.adjustDisplayTime();
        },
        sec: function(val) {
            this.sec = bound(val, 0, 59);
            this.adjustDisplayTime();
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
        adjustDisplayTime() {
            if (this.hr == '' && this.min == '' && this.sec == '') {
                Object.assign(this.$data, timeFactory());
                return;
            }
            this.hr = this.hr == '' ? '00' : this.hr;
            this.sec = this.sec == '' ? '00' : this.sec;
            this.min = this.min == '' ? '00' : this.min;

            if (parseInt(this.hr) > 0) {
                // hr, min focused display
                this.timeHi = this.hr;
                this.timeLo = this.min;
                this.hiLabel = 'hr';
                this.loLabel = 'min';
            }
            else {
                // min, sec focused display
                this.timeHi = this.min;
                this.timeLo = this.sec; 
                this.hiLabel = 'min';
                this.loLabel = 'sec';
            }

            this.hr = this.hr == '00' ? '' : this.hr;
            this.sec = this.sec == '00' ? '' : this.sec;
            this.min = this.min == '00' ? '' : this.min;
        }
    },
}


function timeFactory() {
    return {
            min: '',
            hr: '',
            sec: '',
            timeHi: '00',
            timeLo: '00',
            hiLabel: '',
            loLabel: '',
        };
}

function bound(val, lo, hi) {
    if (val == '') return val;
    val = parseInt(val);
    if (val < lo) val = lo;
    if (val > hi) val = hi;
    return '' + val;
}

</script>




<style scoped>
    .time {
        font-size: 48px;
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
