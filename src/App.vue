<template>
  <div id="app">
    <div class="Drummer">
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
  data() {
    return {
      CurrentStep: 0,
      PatternLength: 1
    };
  },
  methods: {
    HandleClockStep (ClockStep) {
      this.CurrentStep = ClockStep;
    },
    HandlePatternLength (Length) {
      this.PatternLength = Length;
    }
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css?family=Orbitron:500');

html {
  font-size: 10px;
}

body {
  margin: 0;
}

button,
input {
  border: none;
  outline: none;
  cursor: pointer;
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
  padding-top: 8rem;
  padding-bottom: 4rem;
  border-radius: 6px;
  border-left: #6e6b58 1.5rem solid;
  border-right: #6e6b58 1.5rem solid;
  background: #e5dad4;
  font-family: 'Helvetica';
}

</style>
