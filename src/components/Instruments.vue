<template>
  <div class="Instruments">
    <KickDrum :Step="CurrentStep" />
  </div>
</template>

<script>

import KickDrum from './Instruments/KickDrum'

export default {
  name: 'Instruments',
  components: {
    KickDrum
  },
  props: ['Step'],
  data() {
    return {
      CurrentStep: 0
    }
  },
  watch: {
    Step: function (StepValue) {
      this.CurrentStep = StepValue;
    }
  }
}

</script>

<style scoped>

</style>
