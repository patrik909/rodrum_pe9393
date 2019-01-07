<template>
  <audio controls preload="auto" id="LowTom">
    <source src="../../assets/lowtom.mp3" type="audio/mpeg">
  </audio>
</template>

<script>

export default {
  name: 'LowTom',
  props: ['Step', 'Triggers', 'Volume', 'Tune'],
  data () {
    return {
      TriggerSteps: [],
      CurrentStep: 0
    }
  },
  watch: {
    Step: function (StepValue) {
      if (this.TriggerSteps.indexOf(StepValue) > -1) {
        const audio = document.getElementById('LowTom')
        audio.currentTime = 0
        audio.play()
      }
    },
    Triggers: function (Trigg) {
      this.TriggerSteps = Trigg
    },
    Volume: function (Vol) {
      const audio = document.getElementById('LowTom')
      audio.volume = Vol / 100
    },
    Tune: function (TuneVal) {
      const audio = document.getElementById('LowTom')
      audio.playbackRate = TuneVal / 100
    }
  }
}

</script>

<style scoped>

audio {
  display: none;
}

</style>
