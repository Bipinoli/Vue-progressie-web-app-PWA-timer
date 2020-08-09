<template>
    <div class="screen">
        <div class="time">00:<span class="time-lower">00</span></div>
        <div class="btn">NEW</div>
    </div>
</template>


<script>
export default {
    name: 'Default',

}
</script>


<style scoped>
    .time {
        font-size: 96px;
    }

    .btn {
        font-size: 36px;
        color: #17B890;
        border: 1px solid #17B890;
        padding: 10px;
        text-align: center;
        border-radius: 15px;
    }
</style>