<template>
  <audio controls preload="auto" id="SnareDrum">
    <source src="../../assets/snare.mp3" type="audio/mpeg">
  </audio>
</template>

<script>

export default {
  name: 'SnareDrum',
  props: ['Step', 'Triggers'],
  data() {
    return {
      TriggerSteps: [],
      CurrentStep: 0
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
      console.log(Trigg)
      this.TriggerSteps = Trigg;
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
