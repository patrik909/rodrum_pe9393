<template>
  <audio controls preload="auto" id="RimShot">
    <source src="../../assets/rimshot.mp3" type="audio/mpeg">
  </audio>
</template>

<script>

export default {
  name: 'RimShot',
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
        const audio = document.getElementById('RimShot')
        audio.currentTime = 0
        audio.play()
      }
    },
    Triggers: function (Trigg) {
      this.TriggerSteps = Trigg
    },
    Volume: function (Vol) {
      const audio = document.getElementById('RimShot')
      audio.volume = Vol / 100
    },
    Tune: function (TuneVal) {
      const audio = document.getElementById('RimShot')
      audio.playbackRate = TuneVal / 100
    }
  },
  methods: {

  }
}

</script>

<style scoped>

audio {
  display: none;
}

</style>
