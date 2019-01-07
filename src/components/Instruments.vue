<template>
  <div class="Instruments">
    <KickDrum :Volume="KickVolume" :Tune="KickTune" />
    <p>Kick</p>
    Level<input type="range" :value="KickVolume" min="0" max="100" step="1" v-on:input="HandleKickVolume('KickDrum', $event)">
    Tune<input type="range" :value="KickTune" min="50" max="150" step="1" v-on:input="HandleKickTune('KickDrum', $event)">
    <SnareDrum :Volume="SnareVolume" />
    Snare
    <input type="range" :value="SnareVolume" min="0" max="100" step="1" v-on:input="HandleSnareVolume('SnareDrum', $event)"> 
    <ClsdHihat :Volume="ClsdHihatVolume" />
    Hihat
    <input type="range" :value="ClsdHihatVolume" min="0" max="100" step="1" v-on:input="HandleClsdHihatVolume('ClsdHihat', $event)">
    <Ride :Volume="RideVolume" /> 
    Ride
    <input type="range" :value="RideVolume" min="0" max="100" step="1" v-on:input="HandleRideVolume('Ride', $event)">  
  </div>
</template>

<script>

import KickDrum from './Instruments/KickDrum'
import SnareDrum from './Instruments/SnareDrum'
import LowTom from './Instruments/LowTom'
import MidTom from './Instruments/MidTom'
import HiTom from './Instruments/HiTom'
import RimShot from './Instruments/RimShot'
import HandClap from './Instruments/HandClap'
import ClsdHihat from './Instruments/ClsdHihat'
import OpenHihat from './Instruments/OpenHihat'
import Crash from './Instruments/Crash'
import Ride from './Instruments/Ride'

export default {
  name: 'Instruments',
  components: {
    KickDrum,
    SnareDrum,
    LowTom,
    MidTom,
    HiTom,
    RimShot,
    HandClap,
    ClsdHihat,
    OpenHihat,
    Crash,
    Ride
  },
  data() {
    return {
      KickVolume: 50,
      KickTune: 100,
      SnareVolume: 50,
      ClsdHihatVolume: 50,
      RideVolume: 50
    }
  },
  methods: {
    HandleKickVolume(Instrument, Event) {
        this.KickVolume = Event.target.value;
    },
    HandleKickTune(Instrument, Event) {
      this.KickTune = Event.target.value;
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
