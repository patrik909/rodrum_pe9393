<template>
  <audio controls preload="auto" id="Ride">
    <source src="../../assets/ride.mp3" type="audio/mpeg">
  </audio>
</template>

<script>

export default {
  name: 'Ride',
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
        const audio = document.getElementById('Ride');
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
