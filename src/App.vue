<template>
  <div id="app">
    <div class="main">
      <Default v-show="showDefaultScreen" @to-setup="toSetup"></Default>
      <CountdownSetup v-show="showSetupScreen" @to-running="toRunning"></CountdownSetup>
      <CountdownRunning v-show="showRunningScreen" @to-pause="toPause"></CountdownRunning>
      <CountdownPaused v-show="showPauseScreen" @to-stop="toDefault" @to-resume="toResume"></CountdownPaused>
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
      'sec': 0
    };
  },
  methods: {
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
    },
    toResume() {
      this.showPauseScreen = false;
      this.showRunningScreen = true;
    },
    toDefault() {
      this.showPauseScreen = false;
      this.showDefaultScreen = true;
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

</style>
