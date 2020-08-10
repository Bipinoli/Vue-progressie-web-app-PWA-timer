<template>
  <div id="app">
    <div class="main">
      <Default v-if="showDefaultScreen" @to-setup="toSetup" @stop-vibration="stopVibration" :isFinishing="countDownFinished"></Default>
      <CountdownSetup v-if="showSetupScreen" @to-running="toRunning"></CountdownSetup>
      <CountdownRunning v-if="showRunningScreen" @to-pause="toPause" @time-up="timeUp" :hr="hr" :min="min" :sec="sec"></CountdownRunning>
      <CountdownPaused v-if="showPauseScreen" @to-stop="toDefault" @to-resume="toResume" :hr="hr" :min="min" :sec="sec"></CountdownPaused>
    </div>
  </div>
</template>


<script>
import CountdownPaused from './components/CountdownPaused.vue'
import Default from './components/Default.vue'
import CountdownSetup from './components/CountdownSetup.vue'
import CountdownRunning from './components/CountdownRunning.vue'

export default {
  name: 'App',
  components: {
    CountdownPaused,
    Default,
    CountdownSetup,
    CountdownRunning
  },
  data() {
    return {
      showDefaultScreen: true,
      showPauseScreen: false,
      showRunningScreen: false,
      showSetupScreen: false,

      'hr': 0,
      'min': 0,
      'sec': 0,

      'paused': false,
      'countDownFinished': false,

      'vibrator': null,
    };
  },
  created: function() {
    setInterval(() => {
      if (this.paused) return;
      let seconds = this.hr * 60 * 60 + this.min * 60 + this.sec;
      if (seconds == 0) return;
      seconds -= 1;
      this.hr = Math.floor(seconds/(60*60));
      seconds -= this.hr * 60 * 60;
      this.min = Math.floor(seconds/60);
      seconds -= this.min * 60;
      this.sec = seconds; 
    }, 1000);
  },
  methods: {
    timeUp() {
      this.showRunningScreen = false;
      this.countDownFinished = true;
      this.toDefault();
      let isMobile = (/iPhone|iPod|iPad|Android|BlackBerry/).test(navigator.userAgent);
      if (isMobile) {
        this.vibrator = setInterval(() => {
          navigator.vibrate(500);
        }, 750);
      }
      else {
        alert("Time UP! \nI couldn't notify u with vibration.");
      }
    },
    stopVibration() {
      let isMobile = (/iPhone|iPod|iPad|Android|BlackBerry/).test(navigator.userAgent);
      if (isMobile) {
        clearInterval(this.vibrator);
      }
      this.countDownFinished = false;
    },
    toSetup() {
      this.showDefaultScreen = false;
      this.showSetupScreen = true;
    },
    toRunning(setup) {
      this.showSetupScreen = false;
      this.showRunningScreen = true;

      this.hr = setup.hr;
      this.min = setup.min;
      this.sec = setup.sec;
    },
    toPause() {
      this.showRunningScreen = false;
      this.showPauseScreen = true;
      this.paused = true;
    },
    toResume() {
      this.showPauseScreen = false;
      this.showRunningScreen = true;
      this.paused = false;
    },
    toDefault() {
      this.showPauseScreen = false;
      this.showDefaultScreen = true;
      this.paused = false;
      this.hr = 0;
      this.min = 0;
      this.sec = 0;
    }
  }
}


</script>




<style>

body,html {
    margin: 0;
    padding: 0;
    font-family: 'Montserrat', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
* {
    box-sizing: border-box;
}

img {
    height: 100px;
}

.main {
    height: 100vh;
    padding: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.time {
    color: #082D0F;
    text-align: center;
}

.time-lower {
    color: #F96E46;
}

.row {
    display: flex;
    flex-direction: row;
}

.time-control-btn {
    margin-top: 2em;
    display: flex;
    justify-content: center;
    align-items: center;
}

.time-label {
    text-align: center;
    margin-bottom: 4rem;
    font-size: 1.2rem;
    font-weight: 300;
}

</style>
