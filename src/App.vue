<template>
  <div id="app">
    <div class="main">
      <!-- <CountdownPaused></CountdownPaused> -->
      <!-- <Default></Default> -->
      <!-- <CountdownSetup></CountdownSetup> -->
      <CountdownRunning></CountdownRunning>
    </div>
  </div>
</template>

<script>
// import CountdownPaused from './components/CountdownPaused.vue'
// import Default from './components/Default.vue'
// import CountdownSetup from './components/CountdownSetup.vue'
import CountdownRunning from './components/CountdownRunning.vue'

export default {
  name: 'App',
  components: {
    // CountdownPaused,
    // Default,
    // CountdownSetup,
    CountdownRunning
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
