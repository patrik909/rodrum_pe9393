<template>
  <div class="Sequencer">
    <div>
    <div class="SelectInstruments">
      <button v-on:click="ShowSequence(KickSeq, 'KickSeq')"><p>BD</p></button>
      <button v-on:click="ShowSequence(SnareSeq, 'SnareSeq')"><p>SD</p></button>
      <button v-on:click="ShowSequence(ClsdHihatSeq, 'ClsdHihatSeq')"><p>HH</p></button>
      <button v-on:click="ShowSequence(RideSeq, 'RideSeq')"><p>RI</p></button>
    </div>
    </div>
    <div class="StepCounter">
      <div class="Step" v-for="index in PatternLength">
        <div class="LED" v-if="index === CurrentStep"></div>
      </div>
    </div>

    <div class="Audio">
      <KickDrum :Step="CurrentStep" :Triggers="KickSeq" />
      <SnareDrum :Step="CurrentStep" :Triggers="SnareSeq" />
      <ClsdHihat :Step="CurrentStep" :Triggers="ClsdHihatSeq" />
      <Ride :Step="CurrentStep" :Triggers="RideSeq" />
    </div>

    <div id="Triggers">
      <button v-for="index in PatternLength" v-on:click="HandleSequence($event, index)"></button>
    </div>
    <div id="StepIndexes">
      <p v-for="index in PatternLength">{{index}}</p>
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
      DisplayingSeq: 'KickSeq',
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
    ShowSequence (Seq, SeqClass) {
      this.DisplayingSeq = SeqClass

      const TriggerButtons = document.getElementById('Triggers').children;
      for (let i = 0; i < TriggerButtons.length; i++) {
        TriggerButtons[i].classList.remove('Triggered');
      }
      for (let i = 0; i < Seq.length; i++) {
        let index = Seq[i] - 1;
        TriggerButtons[index].classList.add('Triggered');

      }

    },
    HandleSequence (event, TriggerStep) {
      let Seq = [];
      const TriggerButton = event.target;
      TriggerButton.classList.toggle('Triggered');
      if (this.DisplayingSeq === 'KickSeq') {
        Seq = this.KickSeq;
      } else if (this.DisplayingSeq === 'SnareSeq') {
        Seq = this.SnareSeq;
      } else if (this.DisplayingSeq === 'ClsdHihatSeq') {
        Seq = this.ClsdHihatSeq;
      } else if (this.DisplayingSeq === 'RideSeq') {
        Seq = this.RideSeq;
      }

      if (Seq.indexOf(TriggerStep) > -1) {
        if (this.DisplayingSeq === 'KickSeq') {
          this.KickSeq = Seq.filter(value => value !== TriggerStep);
        } else if (this.DisplayingSeq === 'SnareSeq') {
          this.SnareSeq = Seq.filter(value => value !== TriggerStep);
        } else if (this.DisplayingSeq === 'ClsdHihatSeq') {
          this.ClsdHihatSeq = Seq.filter(value => value !== TriggerStep);
        } else if (this.DisplayingSeq === 'RideSeq') {
          this.RideSeq = Seq.filter(value => value !== TriggerStep);
        }
      } else {
        Seq.push(TriggerStep);
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
  transition: 150ms;
}

#Triggers .Triggered {
  background: red;
}

#StepIndexes p {
  padding: 0.4rem 0;
  width: 7.6rem;
  background: #4d565d;
  color: #e5dad4;
  text-align: center;
}

</style>
