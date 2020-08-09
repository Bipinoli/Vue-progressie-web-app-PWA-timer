<template>
    <div class="screen">
        <div class="time">00:<span class="time-lower">00</span></div>
        <div class="time-control-btn" @click="$emit('to-pause')">
            <img src="../assets/pause.svg" alt="pause">
        </div>
    </div>
</template>


<script>
export default {
    name: 'CountdownRunning',
}
</script>


<style scoped>
    .time {
        font-size: 96px;
    }
</style>