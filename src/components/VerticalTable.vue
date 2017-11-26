<template>
  <div class="vertical-table">
    <b-btn v-b-toggle.collapse2 variant="primary" >Toggle Critical Stations</b-btn>
    <b-collapse id="collapse2" class="mt-2">
        <b-table dark hover :items="items">
            <template slot="actions" scope="cell">
            <!-- We use click.stop here to prevent a 'row-clicked' event from also happening -->
            <b-btn size="sm" @click.stop="details(cell.item,cell.index,$event.target)">Details</b-btn>
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
      items: [
        {     critical_stations: 'WHITEHALL JN' },
        {     critical_stations: 'NEWARK NORTH GATE' },
        {     critical_stations: 'GILBERDYKE' },
        {     critical_stations: 'FINSBURY PARK' },
        {     critical_stations: 'TALLINGTON JN' },
      ]
    };
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
        position: absolute;
    }
</style>
