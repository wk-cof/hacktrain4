<template>
  <div class="vertical-table">
    <b-btn v-b-toggle.collapse2 variant="primary" >Toggle Critical Stations</b-btn>
    <b-collapse id="collapse2" class="mt-2">
        <b-table :fields="fields" :items="items">
            <template slot="cs" scope="data">
            <a :href="`#`" v-on:click="linkClicked">
                {{data.item.critical_stations}}
            </a>
            </template>
        </b-table>
    </b-collapse>
  </div>
</template>

<script>
import { EventBus } from '../event-bus.js';

export default {
  name: "verticaltable",
  data() {
    return {
        fields: [
        {
          key: 'cs',
          label: 'Critical Station'
        }],
      items: [
        {     critical_stations: 'WHITEHALL JN' },
        {     critical_stations: 'NEWARK NORTH GATE' },
        {     critical_stations: 'GILBERDYKE' },
        {     critical_stations: 'FINSBURY PARK' },
        {     critical_stations: 'TALLINGTON JN' },
      ]
    };
  },
  methods: {
      linkClicked(args) {
        EventBus.$emit('point-clicked', {
            "Affected_Stanox": 16523,
            "Latitude": 53.7823,
            "Longitude": -1.06197,
            "Number_of_Effects": 41,
            "Delay_Avg": 15,
            "Stanox_Name": "WHITEHALL JN",
            "Train_Service1": "DBC UK: Ketton / Clitheroe - St. Pancras",
            "Train_Service2": "DBC UK: Stud Farm - Bury St. Edmunds / Marks Tey",
            "Train_Service3": "DBC UK: Mountsorrel - Broxbourne",
            "Affected_Operator1": "TPE",
            "Affected_Operator2": "TPE",
            "Affected_Operator3": "EWS",
            "Delay_Time1": 6,
            "Delay_Time2": 11,
            "Delay_Time3": 28,
            "Time_to_Delay1": 13,
            "Time_to_Delay2": 27,
            "Time_to_Delay3": 111,
            "Confidence1": 91,
            "Confidence2": 74,
            "Confidence3": 75
        });
      }
  },
  created: function() {
    // EventBus.$on('point-clicked', point => {
    //     this.items = [
    //     {
    //       train_service: point.Train_Service1,
    //       affected_operator: point.Affected_Operator1,
    //       delay_time: point.Delay_Time1,
    //       time_to_delay: point.Time_to_Delay1,
    //       confidence: point.Confidence1
    //     },
    //     {
    //       train_service: point.Train_Service2,
    //       affected_operator: point.Affected_Operator2,
    //       delay_time: point.Delay_Time2,
    //       time_to_delay: point.Time_to_Delay2,
    //       confidence: point.Confidence2
    //     },
    //     {
    //       train_service: point.Train_Service3,
    //       affected_operator: point.Affected_Operator3,
    //       delay_time: point.Delay_Time3,
    //       time_to_delay: point.Time_to_Delay3,
    //       confidence: point.Confidence3
    //     }
    //   ]
    // });
  }
};
</script>

<style scoped>
    .vertical-table {
        /* position: absolute; */
    }
</style>
