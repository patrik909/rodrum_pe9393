<template>
  <div id="Instruments">
    <div>
      <p>Kick</p>
      <KickDrum :Volume="KickVolume" :Tune="KickTune" />
      Level <input type="range" :value="KickVolume" min="0" max="100" step="1" v-on:input="HandleKickVolume('KickDrum', $event)">
      <!-- Tune<input type="range" :value="KickTune" min="50" max="150" step="1" v-on:input="HandleKickTune('KickDrum', $event)"> -->
    </div>
    <div>
      <p>Snare</p>
      <SnareDrum :Volume="SnareVolume" />
      Level <input type="range" :value="SnareVolume" min="0" max="100" step="1" v-on:input="HandleSnareVolume('SnareDrum', $event)"> 
    </div>
    <div>
      <p>Low tom</p>
      <LowTom :Volume="LowTomVolume" />
      Level <input type="range" :value="LowTomVolume" min="0" max="100" step="1" v-on:input="HandleLowTomVolume('LowTom', $event)">      
    </div>
    <div>
      <p>Mid tom</p>
      <MidTom :Volume="MidTomVolume" />
      Level <input type="range" :value="MidTomVolume" min="0" max="100" step="1" v-on:input="HandleMidTomVolume('MidTom', $event)">      
    </div>
    <div>
      <p>Hi tom</p>
      <HiTom :Volume="HiTomVolume" />
      Level <input type="range" :value="HiTomVolume" min="0" max="100" step="1" v-on:input="HandleHiTomVolume('HiTom', $event)">      
    </div>
    <div>
      <p>Rim shot</p>
      <RimShot :Volume="RimShotVolume" />
      Level <input type="range" :value="RimShotVolume" min="0" max="100" step="1" v-on:input="HandleRimShotVolume('RimShot', $event)">      
    </div>
    <div>
      <p>Hand clap</p>
      <HandClap :Volume="HandClapVolume" />
      Level <input type="range" :value="HandClapVolume" min="0" max="100" step="1" v-on:input="HandleHandClapVolume('HandClap', $event)">      
    </div>
    <div>
      <p>Closed Hihat</p>
      <ClsdHihat :Volume="ClsdHihatVolume" />
      Level <input type="range" :value="ClsdHihatVolume" min="0" max="100" step="1" v-on:input="HandleClsdHihatVolume('ClsdHihat', $event)">      
    </div>
    <div>
      <p>Open Hihat</p>
      <OpenHihat :Volume="OpenHihatVolume" />
      Level <input type="range" :value="OpenHihatVolume" min="0" max="100" step="1" v-on:input="HandleOpenHihatVolume('OpenHihat', $event)">      
    </div>
    <div>
      <p>Crash</p>
      <Crash :Volume="CrashVolume" />
      Level <input type="range" :value="CrashVolume" min="0" max="100" step="1" v-on:input="HandleCrashVolume('Crash', $event)">      
    </div>
    <div>
      <p>Ride</p>
      <Ride :Volume="RideVolume" />
      Level <input type="range" :value="RideVolume" min="0" max="100" step="1" v-on:input="HandleRideVolume('Ride', $event)">      
    </div>


    <!-- <ClsdHihat :Volume="ClsdHihatVolume" />
    Hihat
    <input type="range" :value="ClsdHihatVolume" min="0" max="100" step="1" v-on:input="HandleClsdHihatVolume('ClsdHihat', $event)">
    <Ride :Volume="RideVolume" /> 
    Ride
    <input type="range" :value="RideVolume" min="0" max="100" step="1" v-on:input="HandleRideVolume('Ride', $event)">   -->
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
      LowTomVolume: 50,
      MidTomVolume: 50,
      HiTomVolume: 50,
      RimShotVolume: 50,
      HandClapVolume: 50,
      ClsdHihatVolume: 50,
      OpenHihatVolume: 50,
      CrashVolume: 50,
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

    HandleLowTomVolume(Instrument, Event) {
      this.LowTomVolume = Event.target.value;
    },
    HandleMidTomVolume(Instrument, Event) {
      this.MidTomVolume = Event.target.value;
    },
    HandleHiTomVolume(Instrument, Event) {
      this.HiTomVolume = Event.target.value;
    },

    HandleRimShotVolume(Instrument, Event) {
      this.RimShotVolume = Event.target.value;
    },
    HandleHandClapVolume(Instrument, Event) {
      this.HandClapVolume = Event.target.value;
    },


    HandleClsdHihatVolume(Instrument, Event) {
      this.ClsdHihatVolume = Event.target.value;
    },
    HandleOpenHihatVolume(Instrument, Event) {
      this.OpenHihatVolume = Event.target.value;
    },

    HandleCrashVolume(Instrument, Event) {
      this.CrashVolume = Event.target.value;
    },
    HandleRideVolume(Instrument, Event) {
      this.RideVolume = Event.target.value;
    }
  }
}

</script>

<style>

#Instruments {
  /* display: flex; */
}

#Instruments div {
  /* width: 50px; */
}

input[type=range] {
  /* transform: rotate(270deg); */
}

</style>
