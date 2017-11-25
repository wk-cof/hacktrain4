<template>
  <div class="bg-inverse text-white">
    <div class="text-center">
    </div>
    <progress-bar time="5 min"></progress-bar>
    <gmap-map
    :center="center"
    :zoom="6"
    style="width: 400px; height: 600px"
  >
    <gmap-marker
      :key="index"
      v-for="(m, index) in markers"
      :position="m.position"
      :clickable="true"
      :draggable="true"
      @click="center=m.position"
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
      // mappedData.pop();
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
    }
  },
  created: function() {
    let processedData = this.processData(stanoxData);
    let mappedData = this.createNodes(processedData);
    this.markers = mappedData.splice(0, 500);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#container {
  max-width: 400px;
  height: 400px;
  margin: auto;
}
.header {
  /* background: #292b2c; */
}

.oval1 {
  background-image: linear-gradient(
    -180deg,
    #ffffff 0%,
    #d1dbdc 49%,
    #bbbbbb 100%
  );
  box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.25), 0 1px 3px 0 rgba(0, 0, 0, 0.4),
    inset 0 0 0 0 rgba(255, 255, 255, 0.16);
}
/* Oval 2: */
.oval2 {
  background-image: radial-gradient(
    50% 97%,
    #6bdb5b 23%,
    #58dc39 30%,
    #44bd3a 65%,
    #309f24 98%
  );
}
/* Rectangle-path: */
.rectangle-path {
  background-image: linear-gradient(-180deg, #f4faf8 33%, #d9d8d6 84%);
  box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.36), 0 0 0 0 rgba(36, 36, 36, 0.32),
    inset 0 0 1px 0 #ffffff;
}
</style>
