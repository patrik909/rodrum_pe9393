<template>
  <div class="Sequencer">
    <div>
    <div class="SelectInstruments">
      <button v-on:click="ShowSequence('KickSequence')"><p>BD</p></button>
      <button v-on:click="ShowSequence('SnareSequence')"><p>SD</p></button>
      <button v-on:click="ShowSequence('HihatSequence')"><p>HH</p></button>
      <button v-on:click="ShowSequence('RideSequence')"><p>RI</p></button>
    </div>
    </div>
    <div class="StepCounter">
      <div class="Step" v-for="index in PatternLength">
        <div class="LED" v-if="index === CurrentStep"></div>
      </div>
    </div>

    <div class="Triggers">
      <KickDrum :Step="CurrentStep" :Triggers="KickSeq" />
      <button v-for="index in PatternLength" v-on:click="TriggerKick($event, index)"></button>
    </div>

    <div class="Triggers KickSequence hide">
      <KickDrum :Step="CurrentStep" :Triggers="KickSeq" />
      <button v-for="index in PatternLength" v-on:click="TriggerKick($event, index)"></button>
    </div>
    <div class="Triggers SnareSequence hide">
      <SnareDrum :Step="CurrentStep" :Triggers="SnareSeq" />
      <button v-for="index in PatternLength" v-on:click="TriggerSnare($event, index)"></button>
    </div>
    <div class="Triggers ClsdHihatSequence hide">
      <ClsdHihat :Step="CurrentStep" :Triggers="ClsdHihatSeq" />
      <button v-for="index in PatternLength" v-on:click="TriggerClsdHihat($event, index)"></button>
    </div>
    <div class="Triggers RideSequence hide">
      <Ride :Step="CurrentStep" :Triggers="RideSeq" />
      <button v-for="index in PatternLength" v-on:click="TriggerRide($event, index)"></button>
    </div>
  </div>
</template>

<script>

import KickDrum from './Instruments/KickDrum'
import SnareDrum from './Instruments/SnareDrum'
import ClsdHihat from './Instruments/ClsdHihat'
import Ride from './Instruments/Ride'

export default {
  name: 'Sequencer',
  components: {
    KickDrum,
    SnareDrum,
    ClsdHihat,
    Ride
  },
  props: ['Step'],
  data() {
    return {
      CurrentStep: 0,
      PatternLength: 16,
      KickSeq: [],
      SnareSeq: [],
      LowTomSeq: [],
      MidTomSeq: [],
      HiTomSeq: [],
      RimSeq: [],
      ClapSeq: [],
      ClsdHihatSeq: [],
      OpenHihatSeq: [],
      CymSeq: [],
      RideSeq: [],
    }
  },
  created: function () {
    this.$emit('HandlePatternLength', this.PatternLength);
  },
  watch: {
    Step: function (StepValue) {
      this.CurrentStep = StepValue;
    }
  },
  methods: {
    TriggerKick (event, TriggerValue) {      
      const TriggerButton = event.target;
      TriggerButton.classList.toggle('Triggered');

      if (this.KickSeq.indexOf(TriggerValue) > -1) {
        this.KickSeq = this.KickSeq.filter(value => value !== TriggerValue);
      } else {
        this.KickSeq.push(TriggerValue);
      }
    },
    TriggerSnare (event, TriggerValue) {    

      const TriggerButton = event.target;
      TriggerButton.classList.toggle('Triggered');
      
      if (this.SnareSeq.indexOf(TriggerValue) > -1) {
        this.SnareSeq = this.SnareSeq.filter(value => value !== TriggerValue);
      } else {
        this.SnareSeq.push(TriggerValue);
      }
    },
    TriggerClsdHihat (event, TriggerValue) {    

      const TriggerButton = event.target;
      TriggerButton.classList.toggle('Triggered');
      
      if (this.ClsdHihatSeq.indexOf(TriggerValue) > -1) {
        this.ClsdHihatSeq = this.ClsdHihatSeq.filter(value => value !== TriggerValue);
      } else {
        this.ClsdHihatSeq.push(TriggerValue);
      }
    },
    TriggerRide (event, TriggerValue) {    

      const TriggerButton = event.target;
      TriggerButton.classList.toggle('Triggered');
      
      if (this.RideSeq.indexOf(TriggerValue) > -1) {
        this.RideSeq = this.RideSeq.filter(value => value !== TriggerValue);
      } else {
        this.RideSeq.push(TriggerValue);
      }
    },
    ShowSequence (SeqClass) {
      const Sequences = document.getElementsByClassName('Triggers');
      for (let i = 0; i < Sequences.length; i++) {
        if (Sequences[i].classList[1].indexOf(SeqClass) > -1) {
          Sequences[i].classList.remove('hide');
        } else {
          Sequences[i].classList.add('hide');
        }
      }
    }
  }
}

</script>

<style scoped>

.StepCounter,
.Triggers {
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

.Triggers button {
  margin: 0 1.2rem;
  height: 5.2rem;
  width: 5.2rem;
  border-radius: 0.6rem;
  background: #fdf3da;
  transition: 150ms;
}

.Triggers .Triggered {
  background: red;
}

</style>
