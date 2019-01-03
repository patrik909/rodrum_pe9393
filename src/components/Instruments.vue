<template>
  <div class="Instruments">
    <KickDrum :Volume="KickVolume" />
    Kick
    <input type="range" min="0" max="100" step="1" v-on:input="HandleKickVolume('KickDrum', $event)">
    <SnareDrum :Volume="SnareVolume" />
    Snare
    <input type="range" min="0" max="100" step="1" v-on:input="HandleSnareVolume('SnareDrum', $event)"> 
    <ClsdHihat :Volume="ClsdHihatVolume" />
    Hihat
    <input type="range" min="0" max="100" step="1" v-on:input="HandleClsdHihatVolume('ClsdHihat', $event)">
    <Ride :Volume="RideVolume" /> 
    Ride
    <input type="range" min="0" max="100" step="1" v-on:input="HandleRideVolume('Ride', $event)">  
  </div>
</template>

<script>

import KickDrum from './Instruments/KickDrum'
import SnareDrum from './Instruments/SnareDrum'
import ClsdHihat from './Instruments/ClsdHihat'
import Ride from './Instruments/Ride'

export default {
  name: 'Instruments',
  components: {
    KickDrum,
    SnareDrum,
    ClsdHihat,
    Ride
  },
  data() {
    return {
      KickVolume: 50,
      SnareVolume: 50,
      ClsdHihatVolume: 50,
      RideVolume: 50
    }
  },
  methods: {
    HandleKickVolume(Instrument, Event) {
        this.KickVolume = Event.target.value;
    },
    HandleSnareVolume(Instrument, Event) {
      this.SnareVolume = Event.target.value;
  },
  HandleClsdHihatVolume(Instrument, Event) {
    this.ClsdHihatVolume = Event.target.value;
},
HandleRideVolume(Instrument, Event) {
  this.RideVolume = Event.target.value;
}
  }
}

</script>

<style scoped>

</style>
