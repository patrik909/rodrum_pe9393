<template>
  <audio controls preload="auto" id="SnareDrum">
    <source src="../../assets/snare.mp3" type="audio/mpeg">
  </audio>
</template>

<script>

export default {
  name: 'SnareDrum',
  props: ['Step', 'Triggers', 'Volume', 'Tune'],
  data() {
    return {
      TriggerSteps: [],
      CurrentStep: 0,
    }
  },
  watch: {
    Step: function (StepValue) {
      if (this.TriggerSteps.indexOf(StepValue) > -1) {
        const audio = document.getElementById('SnareDrum');
        audio.currentTime = 0;
        audio.play();
      }
    },
    Triggers: function (Trigg) {
      this.TriggerSteps = Trigg;
    },
    Volume: function (Vol) {
      const audio = document.getElementById('SnareDrum');
      audio.volume = Vol/100;
      // this.InstVolume = Vol;
    },
    Tune: function (TuneVal) {
      console.log(TuneVal)
      const audio = document.getElementById('SnareDrum');

      audio.playbackRate = TuneVal/100;
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
