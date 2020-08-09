<template>
    <div class="screen">
        <div class="time">00:<span class="time-lower">00</span></div>
        <div class="countdown-setup">
            <div class="choice">
                <input type="number" class="min-input" name="" id="" :placeholder="min + ' minutes'">
            </div>
            <div class="row">
                <div class="choice">
                    <input type="number" name="" id="" :placeholder="hr + ' hr'">
                </div>
                <div class="choice">
                    <input type="number" name="" id="" :placeholder="sec + ' sec'">
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
    methods: {
        toRunning() {
            this.$emit('to-running');
        }
    },
    data() {
        return {
            min: '00',
            hr: '00',
            sec: '00',
        }
    }
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
