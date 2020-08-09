<template>
    <div class="screen">
        <div class="time">00:<span class="time-lower">00</span><span class="time-extra">sec</span></div>
        <div class="time-control-btn">
            <img src="../assets/resume.svg" alt="resume" @click="$emit('to-resume')">
        </div>
        <div class="btn" @click="$emit('to-stop')">
            stop
        </div>
    </div>
</template>



<script>
export default {
    name: 'CountdownPaused',
};
</script>



<style scoped>
    .screen {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .time {
        padding-left: 0.8em;
        font-size: 72px;
    }

    .time-extra {
        font-size: 36px;
        color: #F96E46;
    }

    .btn {
        border-radius: 15px;
        border: 1.1px solid #F96E46;
        color: #F96E46;
        font-size: 48px;
        text-transform: uppercase;
        margin-top: 4rem;
        text-align: center;
        width: fit-content;
        padding: 10px 20px 10px 20px;
    }
</style>