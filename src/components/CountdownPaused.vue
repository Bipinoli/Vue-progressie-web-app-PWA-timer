<template>
    <div class="screen">
        <div class="time">00:<span class="time-lower">00</span></div>
        <div class="time-label">{{hiLabel}} {{loLabel}}</div>
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
    data: function() {
        return {
            hiLabel: 'min',
            loLabel: 'sec',
        };
    }
};
</script>



<style scoped>
    .screen {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .time {
        font-size: 72px;
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