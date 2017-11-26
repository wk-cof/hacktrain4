<template>
  <div class="bg-inverse text-white outer-dashboard">
        <div class="middle-dashboard">
            <img src="../assets/logo.png" width="250" height="250" alt="qwer">
            <h1 style="margin-left: 50px" class="text-success"> Geo-Incident</h1>
            <div class="bg-inverse text-white my-dashboard" v-show="displayInfographics">
                <div class="my-infographics">
                    <h2>{{time}} minutes</h2>
                    <p class="text-muted">Average delay time</p>
                </div>
                <progress-bar :time="time" station="London Station"></progress-bar>
                <div class="my-infographics">
                    <h2>{{probability}}%</h2>
                    <p class="text-muted">Delay probability</p>
                </div>
            </div>
        </div>
        <!-- <input type="text" placeholder="  Select a train from the TRUST DATABASE"> -->
        <b-form inline v-show="!displayInfographics">
            <b-input id="trainInputTypeInput" style="min-width: 550px"
                v-model="trainInputType"
                placeholder="  Select a train from the TRUST DATABASE" />
            <b-button variant="success">Search</b-button>
        </b-form>
        <b-form-select v-show="!displayInfographics" v-model="dropdown.selected" :options="dropdown.options" class="mb-3">
        </b-form-select>
  </div>
</template>

<script>
import ProgressBar from "./ProgressBar";
import { EventBus } from '../event-bus.js';

export default {
  name: "dashboard",
  data() {
    return {
        time: 5,
        probability: 65,
        trainInputType: '',
        dropdown: {
            selected: '',
            options: [
                { value: '', text: 'Incident type' },
                { value: '1', text: 'This is First option' },
                { value: '2', text: 'Selected Option' },
                { value: '3', text: 'Third Option' }
            ]
        }
    };
  },
  computed: {
      displayInfographics: function() {
          if (!!this.trainInputType && !!this.dropdown.selected) {
            EventBus.$emit('show-small-map', true);
          }
          return !!this.trainInputType && !!this.dropdown.selected;
      }
  },
  components: {
    "progress-bar": ProgressBar
  },
  created: function() {
      EventBus.$on('point-clicked', metadata => {
          this.time = Math.floor(metadata.delayAvg * 100) / 100;
          this.probability = Math.floor(metadata.numberOfEffects / 12 * 100);
      });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.my-infographics {
    display: flex;
    flex-direction: column;
    align-items: center;
    align-content: space-around;
    margin-right: 15px;

}
.outer-dashboard {
    display: flex;
    flex-direction: column;
}
.middle-dashboard {
  display: flex;
  align-items: center;
  margin-bottom: 15px;
}
.my-dashboard {
  display: flex;
  align-items: center;
  justify-content: space-around;
  margin-left: 350px;
}
</style>
