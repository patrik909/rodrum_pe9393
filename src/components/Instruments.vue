<template>
  <div id="Instruments">
    <div class="InstHolder">
      <h4>Bass Drum</h4>
      <KickDrum :Volume="KickVolume" :Tune="KickTune" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="KickVolume" min="0" max="100" step="1" v-on:input="HandleKickVolume('KickDrum', $event)">
        <!-- Tune<input type="range" :value="KickTune" min="50" max="150" step="1" v-on:input="HandleKickTune('KickDrum', $event)"> -->
      </div>
    </div>
    <div class="InstHolder">
      <h4>Snare Drum</h4>
      <SnareDrum :Volume="SnareVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="SnareVolume" min="0" max="100" step="1" v-on:input="HandleSnareVolume('SnareDrum', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Low tom</h4>
      <LowTom :Volume="LowTomVolume" />
      <div class="SliderHolder">
      <p>Level</p>
      <input type="range" :value="LowTomVolume" min="0" max="100" step="1" v-on:input="HandleLowTomVolume('LowTom', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Mid tom</h4>
      <MidTom :Volume="MidTomVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="MidTomVolume" min="0" max="100" step="1" v-on:input="HandleMidTomVolume('MidTom', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Hi tom</h4>
      <HiTom :Volume="HiTomVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="HiTomVolume" min="0" max="100" step="1" v-on:input="HandleHiTomVolume('HiTom', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Rim shot</h4>
      <RimShot :Volume="RimShotVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="RimShotVolume" min="0" max="100" step="1" v-on:input="HandleRimShotVolume('RimShot', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Hand clap</h4>
      <HandClap :Volume="HandClapVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="HandClapVolume" min="0" max="100" step="1" v-on:input="HandleHandClapVolume('HandClap', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Closed Hihat</h4>
      <ClsdHihat :Volume="ClsdHihatVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="ClsdHihatVolume" min="0" max="100" step="1" v-on:input="HandleClsdHihatVolume('ClsdHihat', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Open Hihat</h4>
      <OpenHihat :Volume="OpenHihatVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="OpenHihatVolume" min="0" max="100" step="1" v-on:input="HandleOpenHihatVolume('OpenHihat', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Crash</h4>
      <Crash :Volume="CrashVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="CrashVolume" min="0" max="100" step="1" v-on:input="HandleCrashVolume('Crash', $event)">
      </div>
    </div>
    <div class="InstHolder">
      <h4>Ride</h4>
      <Ride :Volume="RideVolume" />
      <div class="SliderHolder">
        <p>Level</p>
        <input type="range" :value="RideVolume" min="0" max="100" step="1" v-on:input="HandleRideVolume('Ride', $event)">
      </div>
    </div>
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
  data () {
    return {
      KickVolume: 80,
      KickTune: 100,
      SnareVolume: 80,
      LowTomVolume: 80,
      MidTomVolume: 80,
      HiTomVolume: 80,
      RimShotVolume: 80,
      HandClapVolume: 80,
      ClsdHihatVolume: 80,
      OpenHihatVolume: 80,
      CrashVolume: 80,
      RideVolume: 80
    }
  },
  methods: {
    HandleKickVolume (Instrument, Event) {
      this.KickVolume = Event.target.value
    },
    HandleKickTune (Instrument, Event) {
      this.KickTune = Event.target.value
    },

    HandleSnareVolume (Instrument, Event) {
      this.SnareVolume = Event.target.value
    },

    HandleLowTomVolume (Instrument, Event) {
      this.LowTomVolume = Event.target.value
    },
    HandleMidTomVolume (Instrument, Event) {
      this.MidTomVolume = Event.target.value
    },
    HandleHiTomVolume (Instrument, Event) {
      this.HiTomVolume = Event.target.value
    },

    HandleRimShotVolume (Instrument, Event) {
      this.RimShotVolume = Event.target.value
    },
    HandleHandClapVolume (Instrument, Event) {
      this.HandClapVolume = Event.target.value
    },

    HandleClsdHihatVolume (Instrument, Event) {
      this.ClsdHihatVolume = Event.target.value
    },
    HandleOpenHihatVolume (Instrument, Event) {
      this.OpenHihatVolume = Event.target.value
    },

    HandleCrashVolume (Instrument, Event) {
      this.CrashVolume = Event.target.value
    },
    HandleRideVolume (Instrument, Event) {
      this.RideVolume = Event.target.value
    }
  }
}

</script>

<style>

#Instruments {
  display: flex;
  margin: 0rem 1.2rem 6rem 1.2rem;
  height: 16rem;
}

.InstHolder {
  display: flex;
  flex-direction: column;
  align-items: center;
  border-left: 1px solid #4d565d;
  margin-right: 0.2rem;
  width: 10.5rem;
}

.InstHolder h4 {
  margin: 0;
  padding: 0.5rem 0;
  background: #4d565d;
  color: #eb7920;
  width: 100%;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 0.3px;
}

.SliderHolder {
  position: relative;
  padding: 0 1rem;
}

.SliderHolder p {
  text-transform: uppercase;
  font-size: 0.9rem;
}

input[type=range] {
  position: absolute;
  top: 8rem;
  left: -3.45rem;
  -webkit-appearance: none;
  background: #3c4449;
  height: 1rem;
  width: 11rem;
  transform: rotate(270deg);
}

input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 20px;
    height: 15px;
    background: white;
    border-radius: 0.3rem;
    border-left: 9px solid #666666;
    border-right: 9px solid #666666;
}

</style>
