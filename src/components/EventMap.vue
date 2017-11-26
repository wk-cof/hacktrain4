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
import stanoxData from "../data/stanox";
import delayInstance from "../data/delayInstance";
import _ from "lodash";

export default {
  name: "eventmap",
  data() {
    return {
      center: {lat: 54.0, lng: -2.0},

      markers: [
      ]
    };
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
    },
    getAffectedNodes() {
      return _.map(delayInstance, item => {
        return item['Affected_Stanox'];
      });
    },
    getCoordinatesOfAffectedNodes(data, affectedNodes) {
      return _.filter(data, item => {
        return affectedNodes.includes(item[0]);
      });
    }
  },
  created: function() {
    let processedData = this.processData(stanoxData);
    let affectedNodes = this.getAffectedNodes(delayInstance);
    let things = this.getCoordinatesOfAffectedNodes(processedData, affectedNodes);
    this.markers = this.createNodes(things);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
