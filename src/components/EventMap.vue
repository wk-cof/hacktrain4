<template>
  <div>
    <div style="display: flex;">
      <vertical-table class='vertical-table'></vertical-table>
      &nbsp;&nbsp;
      <horizontal-table></horizontal-table>
    </div>
      <gmap-map
        :center="center"
        :zoom="6"
        style="width: 1200px; height: 600px"
      >
        <gmap-marker
          :key="index"
          v-for="(m, index) in markers"
          :position="m.position"
          :clickable="true"
          :draggable="false"
          @click="processClick(markers[index])"
        ></gmap-marker>
      </gmap-map>
  </div>
</template>

<script>
import delayInstance from "../data/delayInstance4";
import _ from "lodash";
import { EventBus } from '../event-bus.js';
import HorizontalTable from './HorizontalTable';
import VerticalTable from './VerticalTable';

export default {
  name: "eventmap",
  data() {
    return {
      center: {lat: 54.0, lng: -2.0},
      markers: []
    };
  },
  methods: {
    processClick(marker) {
      // console.log(metadata.metadata);
      EventBus.$emit('point-clicked', marker.metadata);
    },
    formatInput() {
      return _.map(delayInstance, item => {
        return {
          position: {
            lat: item.Latitude,
            lng: item.Longitude
          },
          metadata: item
        };
      })
    }
  },
  created: function() {
    this.markers = this.formatInput();
  },
  components: {
    'horizontal-table': HorizontalTable,
    'vertical-table': VerticalTable
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.outer-div {
  display: flex;
  flex-direction: row;
}
.vertical-table {
  /* position: aboslute;
  left: 150px; */
}
</style>
