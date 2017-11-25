<template>
  <div>
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
      :draggable="true"
      @click="processClick(index)"
    ></gmap-marker>
  </gmap-map>
  </div>
</template>

<script>
import ProgressBar from './ProgressBar';
import stanoxData from "../data/stanox";
import _ from "lodash";

export default {
  name: "home",
  data() {
    return {
      center: {lat: 54.0, lng: -2.0},

      markers: [
        {
          position: {lat: 54.0, lng: -2.0}
        }
      ]
    };
  },
  components: {
    'progress-bar': ProgressBar
  },
  methods: {
    createNodes(data) {
      let iterator = 0;
      let mappedData = _.map(data, (dataPoint, idx) => {
        iterator++;
        return {
          position: {
            lat: parseFloat(dataPoint[1]),
            lng: parseFloat(dataPoint[2])
          }
        };
      });
      return mappedData;
    },
    processData(allText) {
      let allTextLines = allText.split(/\r\n|\n/);
      allTextLines.splice(0, 1);
      let lines = [];
      while (allTextLines.length > 0) {
        let [currentLine] = allTextLines.splice(0, 1);
        lines.push(currentLine.split(","));
      }
      return lines;
    },
    processClick(idx) {
        alert('Pin ' + idx + ' was clicked');
    }
  },
  created: function() {
    let processedData = this.processData(stanoxData);
    let mappedData = this.createNodes(processedData);
    this.markers = _.shuffle(mappedData).splice(0, 500);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
