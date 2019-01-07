<template>
  <div id="app">
    <div class="Drummer">
      <header>
        <h1>RODRUM</h1>
        <div>
          <h2>PE-9393</h2>
          <h2>WEBBROWSER COMPOSER</h2>
        </div>
      </header>
      <Instruments :Step="CurrentStep" />
      <Clock @HandleClockStep="HandleClockStep" :Length="PatternLength" />
      <Sequencer @HandlePatternLength="HandlePatternLength" :Step="CurrentStep" /></div>
  </div>
</template>

<script>

import Clock from './components/Clock'
import Sequencer from './components/Sequencer'
import Instruments from './components/Instruments'

export default {
  name: 'Drummer',
  components: {
    Clock,
    Sequencer,
    Instruments
  },
  data () {
    return {
      CurrentStep: 0,
      PatternLength: 1
    }
  },
  methods: {
    HandleClockStep (ClockStep) {
      this.CurrentStep = ClockStep
    },
    HandlePatternLength (Length) {
      this.PatternLength = Length
    }
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css?family=Orbitron:500');

html {
  font-size: 8px;
}

body {
  margin: 0;
  background: #d8d8d8;
}

button,
input {
  border: none;
  outline: none;
  cursor: pointer;
}

div {
  position: relative;
}

.hide {
  display: none !important;
}

#app {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.Drummer {
  display: flex;
  flex-direction: column;
  padding: 3rem 1rem 4rem 1rem;
  border-radius: 6px;
  border-left: #6e6b58 1.5rem solid;
  border-right: #6e6b58 1.5rem solid;
  box-shadow: 0px 0px 80px -30px rgba(0,0,0,1);
  background: #e5dad4;
  font-family: 'Helvetica';
}

h1 {
  margin-left: 1.2rem;
  color: #c48961;
  font-size: 4rem;
}

h2 {
  margin: 2rem 0;
  font-size: 2.5rem;
}

header div {
  display: flex;
  justify-content: space-between;
  margin: 0 1.4rem;
  color: #4d565d;
}

@media screen and (orientation: portrait) {
  .Drummer {
    transform: rotate(90deg);
  }
}

@media screen and (max-width: 600px) {
  html {
    font-size: 4.5px;
  }
}

@media screen and (min-width: 600px) and (orientation: portrait) {
    html {
    font-size: 7.5px;
  }
}

@media screen and (min-width: 600px) and (orientation: portrait) {
    html {
    font-size: 9px;
  }
}

</style>
