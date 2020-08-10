<template>
    <div class="screen">
        <div class="time">{{timeHi}}:<span class="time-lower">{{timeLo}}</span></div>
        <div class="time-label">{{hiLabel}} {{loLabel}}</div>
        <div class="time-control-btn">
            <img src="../assets/pause.svg" alt="pause" @click="$emit('to-pause')">
        </div>
    </div>
</template>


<script>
export default {
    name: 'CountdownRunning',
    props: {
        hr: Number,
        min: Number,
        sec: Number
    },
    data: function(){
        return {
            timeHi: '00',
            timeLo: '00',
            hiLabel: 'min',
            loLabel: 'sec',
        };
    },
    watch: {
        hr: function() {
            this.adjustDisplayTime();
        },
        min: function() {
            this.adjustDisplayTime();
        },
        sec: function() {
            this.adjustDisplayTime();
        }
    },
    created: function() {
        this.adjustDisplayTime();
    },
    methods: {
        adjustDisplayTime() {
            if (this.hr > 0) {
                // hr, min format
                this.timeHi = sanitize('' + this.hr);
                this.timeLo = sanitize('' + this.min);
                this.hiLabel = 'hr';
                this.loLabel = 'min';
            } else {
                // min, sec format
                this.timeHi = sanitize('' + this.min);
                this.timeLo = sanitize('' + this.sec);
                this.hiLabel = 'min';
                this.loLabel = 'sec';
            }
        },
    }
}

function sanitize(val) {
    if (val.length == 1)
        return `0${val}`;
    return val;
}

</script>


<style scoped>
    .time {
        font-size: 96px;
    }
</style>