<template>
  <div class="about">
    <b-btn v-b-toggle.collapse1 variant="primary">Toggle Detailed Lines</b-btn>
    <b-collapse id="collapse1" class="mt-2">
        <!-- <b-card> -->
            <b-table hover :items="items"></b-table>
        <!-- </b-card> -->
    </b-collapse>
  </div>
</template>

<script>
import { EventBus } from '../event-bus.js';

export default {
  name: "horizontaltable",
  data() {
    return {
      items: [
        {
          train_service: true,
          affected_operator: 40,
          delay_time: "Dickerson",
          time_to_delay: "Macdonald",
          confidence: "70%"
        }
      ]
    };
  },
  created: function() {
    EventBus.$on('point-clicked', point => {
        this.items = [
        {
          train_service: point.Train_Service1,
          affected_operator: point.Affected_Operator1,
          delay_time: point.Delay_Time1,
          time_to_delay: point.Time_to_Delay1,
          confidence: point.Confidence1
        },
        {
          train_service: point.Train_Service2,
          affected_operator: point.Affected_Operator2,
          delay_time: point.Delay_Time2,
          time_to_delay: point.Time_to_Delay2,
          confidence: point.Confidence2
        },
        {
          train_service: point.Train_Service3,
          affected_operator: point.Affected_Operator3,
          delay_time: point.Delay_Time3,
          time_to_delay: point.Time_to_Delay3,
          confidence: point.Confidence3
        }
      ]
    });
  }
};
</script>

<style scoped>

</style>
