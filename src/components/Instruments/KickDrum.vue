<template>
  <audio controls preload="auto" id="BassDrum">
    <source src="../../assets/kick.mp3" type="audio/mpeg">
  </audio>
</template>

<script>

export default {
  name: 'KickDrum',
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
        const audio = document.getElementById('BassDrum');
        audio.currentTime = 0;
        audio.play();
      }
    },
    Triggers: function (Trigg) {
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
