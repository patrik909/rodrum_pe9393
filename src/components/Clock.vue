<template>
  <div class="Clock">
    <div class="ClockButtons">
      <div>
        <p>Start</p>
        <button v-on:click="StartButton"></button>
      </div>
      <div>
        <p>Stop/Cont</p>
        <button v-on:click="StopButton"></button>
      </div>
    </div>
    <div class="BPM">
      <p>Meas/Tempo</p>
      <input 
        type="text" 
        v-on:change="HandleBPM"
        :value="BPM"
      /> 
      <div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Clock',
  props: ['Length'],
  data() {
    return {
      BPM: 120,
      PatternLength: 1,
      CurrentStep: 0,
      IsClockRunning: false
    };
  },
  created: function () {
      window.addEventListener('keydown', (event) => {
        if (event.keyCode == '32') {
          this.StartButton ()
        }
      });
  },
  watch: {
    Length: function (LengthValue) {
      this.PatternLength = LengthValue;
    }
  },
  methods: {
    StartButton (event) {
      if (this.IsClockRunning) {
        // Pause Timeout.
        clearTimeout(this.Clock);
        // Set Clock not running.
        this.IsClockRunning = false;
        this.$emit('HandleClockStep', this.CurrentStep);
      } else {
        this.RunClock();
      }
    },
    StopButton (event) {
      // Pause Timeout.
      clearTimeout(this.Clock);
      // Reset Clock step counter.
      this.CurrentStep = 0;
      // Set Clock not running.
      this.IsClockRunning = false;
      this.$emit('HandleClockStep', this.CurrentStep);
    },
    RunClock () {
      // Set clock running.
      this.IsClockRunning = true;
      if (this.CurrentStep >= this.PatternLength) {
        // Reset Clock step counter.
        this.CurrentStep = 1;
      } else {
        // Add 1 to current step to move Clock forward.
        this.CurrentStep = this.CurrentStep + 1;
      }
      this.$emit('HandleClockStep', this.CurrentStep);
      // 1min / BPM / steps in one beat.
      this.Clock = setTimeout(() => {
        this.RunClock()
      }, 60000/this.BPM/4);
    },
    HandleBPM (event) {
      const NewBPM = parseInt(event.target.value);
      this.BPM = NewBPM;
    }
  }
}

</script>

<style scoped>

.Clock {
  display: flex;
}

p {
  font-size: 0.8rem;
  text-align: center;
  text-transform: uppercase;
}

.ClockButtons {
  display: flex;
}

.ClockButtons div {
  margin: 0 1.2rem;
}

.ClockButtons button {
  height: 5.2rem;
  width: 5.2rem;
  border-radius: 0.6rem;
  background: #fdf3da;
  box-shadow: 0 2px #c4bca8;
  border: 1px solid #ddd4bc;
  border-bottom: none;
  transition: 150ms;
}

.ClockButtons button:hover {
  background: #f2e8d0;
}

.BPM {
  display: flex;
  flex-direction: column;
  width: 11rem;
  margin-left: 1.5rem;
}

.BPM input {
  padding-top: 0.8rem;
  height: 100%;
  background: black;
  color: red;
  font-family: 'Orbitron', sans-serif;
  font-size: 2.6rem;
  letter-spacing: 0.1rem;
  text-align: center;
}

</style>
