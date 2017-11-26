<template>
  <div>
    <horizontal-table></horizontal-table>
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
import delayInstance from "../data/delayInstance3";
import _ from "lodash";
import { EventBus } from '../event-bus.js';
import HorizontalTable from './HorizontalTable';

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
            lat: parseFloat(item.Latitude),
            lng: parseFloat(item.Longitude)
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
    'horizontal-table': HorizontalTable
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
