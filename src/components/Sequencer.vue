<template>
  <div class="Sequencer">
    <div>
    <div id="SelectInstruments">
      <div id="SelectInstrumentsTitle">
        <div class="line"></div><p>Select instrument</p><div class="line"></div>
      </div>
      <div id="InstrumentButtons">
        <button class="Active" v-on:click="ShowSequence(KickSeq, 'KickSeq', $event)">BD</button>
        <button v-on:click="ShowSequence(SnareSeq, 'SnareSeq', $event)">SD</button>
        <button v-on:click="ShowSequence(LowTomSeq, 'LowTomSeq', $event)">LT</button>
        <button v-on:click="ShowSequence(MidTomSeq, 'MidTomSeq', $event)">MT</button>
        <button v-on:click="ShowSequence(HiTomSeq, 'HiTomSeq', $event)">HT</button>
        <button v-on:click="ShowSequence(RimShotSeq, 'RimShotSeq', $event)">RS</button>
        <button v-on:click="ShowSequence(HandClapSeq, 'HandClapSeq', $event)">CP</button>
        <button v-on:click="ShowSequence(ClsdHihatSeq, 'ClsdHihatSeq', $event)">CH</button>
        <button v-on:click="ShowSequence(OpenHihatSeq, 'OpenHihatSeq', $event)">OH</button>
        <button v-on:click="ShowSequence(CrashSeq, 'CrashSeq', $event)">CR</button>
        <button v-on:click="ShowSequence(RideSeq, 'RideSeq', $event)">RI</button>
      </div>
    </div>
    </div>
    <div class="StepCounter">
      <div class="Step" v-for="index in PatternLength" v-bind:key="index">
        <div class="LED" v-if="index === CurrentStep"></div>
      </div>
    </div>

    <div class="Audio">
      <KickDrum :Step="CurrentStep" :Triggers="KickSeq" />
      <SnareDrum :Step="CurrentStep" :Triggers="SnareSeq" />
      <LowTom :Step="CurrentStep" :Triggers="LowTomSeq" />
      <MidTom :Step="CurrentStep" :Triggers="MidTomSeq" />
      <HiTom :Step="CurrentStep" :Triggers="HiTomSeq" />
      <RimShot :Step="CurrentStep" :Triggers="RimShotSeq" />
      <HandClap :Step="CurrentStep" :Triggers="HandClapSeq" />
      <ClsdHihat :Step="CurrentStep" :Triggers="ClsdHihatSeq" />
      <OpenHihat :Step="CurrentStep" :Triggers="OpenHihatSeq" />
      <Crash :Step="CurrentStep" :Triggers="CrashSeq" />
      <Ride :Step="CurrentStep" :Triggers="RideSeq" />
    </div>

    <div id="Triggers">
      <button v-for="index in PatternLength" v-on:click="HandleSequence($event, index)" v-bind:key="index"></button>
    </div>
    <div id="StepIndexes">
      <p v-for="index in PatternLength" v-bind:key="index">{{index}}</p>
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
  name: 'Sequencer',
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
  props: ['Step'],
  data () {
    return {
      CurrentStep: 0,
      PatternLength: 16,
      DisplayingSeq: 'KickSeq',
      KickSeq: [],
      SnareSeq: [],
      LowTomSeq: [],
      MidTomSeq: [],
      HiTomSeq: [],
      RimShotSeq: [],
      HandClapSeq: [],
      ClsdHihatSeq: [],
      OpenHihatSeq: [],
      CrashSeq: [],
      RideSeq: []
    }
  },
  created: function () {
    this.$emit('HandlePatternLength', this.PatternLength)
  },
  watch: {
    Step: function (StepValue) {
      this.CurrentStep = StepValue
    }
  },
  methods: {
    ShowSequence (Seq, SeqClass, event) {
      const InstButtons = document.getElementById('InstrumentButtons').children
      for (let i = 0; i < InstButtons.length; i++) {
        InstButtons[i].classList.remove('Active')
      }
      event.target.classList.add('Active')

      this.DisplayingSeq = SeqClass

      const TriggerButtons = document.getElementById('Triggers').children
      for (let i = 0; i < TriggerButtons.length; i++) {
        TriggerButtons[i].classList.remove('Triggered')
      }
      for (let i = 0; i < Seq.length; i++) {
        let index = Seq[i] - 1
        TriggerButtons[index].classList.add('Triggered')
      }
    },
    HandleSequence (event, TriggerStep) {
      let Seq = []
      const TriggerButton = event.target
      TriggerButton.classList.toggle('Triggered')

      if (this.DisplayingSeq === 'KickSeq') {
        Seq = this.KickSeq
      } else if (this.DisplayingSeq === 'SnareSeq') {
        Seq = this.SnareSeq
      } else if (this.DisplayingSeq === 'LowTomSeq') {
        Seq = this.LowTomSeq
      } else if (this.DisplayingSeq === 'MidTomSeq') {
        Seq = this.MidTomSeq
      } else if (this.DisplayingSeq === 'HiTomSeq') {
        Seq = this.HiTomSeq
      } else if (this.DisplayingSeq === 'HandClapSeq') {
        Seq = this.HandClapSeq
      } else if (this.DisplayingSeq === 'RimShotSeq') {
        Seq = this.RimShotSeq
      } else if (this.DisplayingSeq === 'ClsdHihatSeq') {
        Seq = this.ClsdHihatSeq
      } else if (this.DisplayingSeq === 'OpenHihatSeq') {
        Seq = this.OpenHihatSeq
      } else if (this.DisplayingSeq === 'CrashSeq') {
        Seq = this.CrashSeq
      } else if (this.DisplayingSeq === 'RideSeq') {
        Seq = this.RideSeq
      }

      if (Seq.indexOf(TriggerStep) > -1) {
        if (this.DisplayingSeq === 'KickSeq') {
          this.KickSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'SnareSeq') {
          this.SnareSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'LowTomSeq') {
          this.LowTomSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'MidTomSeq') {
          this.MidTomSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'HiTomSeq') {
          this.HiTomSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'HandClapSeq') {
          this.HandClapSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'RimShotSeq') {
          this.RimShotSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'ClsdHihatSeq') {
          this.ClsdHihatSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'OpenHihatSeq') {
          this.OpenHihatSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'CrashSeq') {
          this.CrashSeq = Seq.filter(value => value !== TriggerStep)
        } else if (this.DisplayingSeq === 'RideSeq') {
          this.RideSeq = Seq.filter(value => value !== TriggerStep)
        }
      } else {
        Seq.push(TriggerStep)
      }
    }
  }
}

</script>

<style scoped>

.StepCounter,
#Triggers,
#StepIndexes {
  display: flex;
}

.StepCounter .Step {
  margin: 3rem 2.2rem 0.6rem 2.2rem;
  height: 1rem;
  width: 3.2rem;
  background: white;
  border-radius: 10%;
}

.StepCounter .Step .LED {
  height: 100%;
  width: 100%;
  border-radius: 10%;
  background: red;
 }

#Triggers button {
  margin: 0 1.2rem;
  height: 5.2rem;
  width: 5.2rem;
  border-radius: 0.6rem;
  background: #fdf3da;
  box-shadow: 0 2px #c4bca8;
  border: 1px solid #ddd4bc;
  border-bottom: none;
  transition: 150ms;
}

#Triggers button:hover {
  background: #f2e8d0;
}

#Triggers .Triggered {
  background: red !important;
}

#StepIndexes p {
  padding: 0.4rem 0;
  width: 7.6rem;
  background: #4d565d;
  color: #e5dad4;
  text-align: center;
}

#StepIndexes p:first-child {
  margin-left: 1.2rem;
  width: 6.4rem;
}

#StepIndexes p:last-child {
  margin-right: 1.2rem;
  width: 6.4rem;
}

#SelectInstruments {
  display: flex;
  flex-direction: column;
  position: absolute;
  top: -7.7rem;
  right: 1.2rem;
  height: 7.7rem;
}

#SelectInstrumentsTitle {
  display: flex;
  height: 3.5rem;
}

#SelectInstrumentsTitle p {
  margin: 0.6rem 1rem;
  font-size: 0.8rem;
  text-align: center;
  text-transform: uppercase;
  white-space: nowrap;
}

#SelectInstrumentsTitle .line {
  border-top: 1px solid black;
  margin-top: 1rem;
  height: 30%;
  width: 100%;
}

#SelectInstrumentsTitle .line:first-child {
  border-left: 1px solid black;
}

#SelectInstrumentsTitle .line:last-child {
  border-right: 1px solid black;
}

#InstrumentButtons {
  display: flex;
  justify-content: flex-end;
  height: 4.2rem;
  width: 100%;
}

#InstrumentButtons button {
  height: 100%;
  width: 5.2rem;
  margin: 0 1.2rem;
  background: black;
  color: #e5dad4;
  font-size: 1.2rem;
  font-weight: 700;
  letter-spacing: 0.1rem;
  border-radius: 0.6rem;
  transition: 150ms;
}

#InstrumentButtons button:hover {
  background: #3c4449;
}

#InstrumentButtons button:first-child {
  margin-left: 0;
}

#InstrumentButtons button:last-child {
  margin-right: 0;
}

#InstrumentButtons button.Active {
  box-shadow: inset 0 0 4px rgba(0, 0, 0, 0.4);
  background: #4d565d;
}

</style>
