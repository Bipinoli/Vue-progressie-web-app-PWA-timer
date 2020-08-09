<template>
    <div class="screen">
        <div class="time">00:<span class="time-lower">00</span></div>
        <div class="countdown-setup">
            <div class="choice">00 minutes</div>
            <div class="row">
                <div class="choice">00 hr</div>
                <div class="choice">00 sec</div>
            </div>
        </div>
        <div class="time-control-btn" @click="toRunning">
            <img src="../assets/resume.svg" alt="resume">
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
    }
}
</script>


<style scoped>
    .time {
        font-size: 48px;
        margin-bottom: 1.2em;
    }

    .choice {
        padding: 10px 20px 10px 20px;
        border: 1.1px solid #082D0F;
        border-radius: 15px;
        margin: 10px 5px 10px 5px;
        text-align: center;
    }

</style>