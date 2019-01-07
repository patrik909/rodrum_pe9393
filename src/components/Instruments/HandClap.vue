<template>
  <audio controls preload="auto" id="HandClap">
    <source src="../../assets/handclap.mp3" type="audio/mpeg">
  </audio>
</template>

<script>

export default {
  name: 'HandClap',
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
        const audio = document.getElementById('HandClap')
        audio.currentTime = 0
        audio.play()
      }
    },
    Triggers: function (Trigg) {
      this.TriggerSteps = Trigg
    },
    Volume: function (Vol) {
      const audio = document.getElementById('HandClap')
      audio.volume = Vol / 100
    },
    Tune: function (TuneVal) {
      const audio = document.getElementById('HandClap')
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
