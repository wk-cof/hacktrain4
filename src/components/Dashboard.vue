<template>
  <div class="bg-inverse text-white outer-dashboard">
    <img src="../assets/logo.png" width="150" height="150" alt="qwer">
    <div class="bg-inverse text-white my-dashboard">
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
</template>

<script>
import ProgressBar from "./ProgressBar";

export default {
  name: "dashboard",
  data() {
    return {
        time: 5,
        probability: 65
    };
  },
  components: {
    "progress-bar": ProgressBar
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
  align-items: center;
}
.my-dashboard {
  display: flex;
  align-items: center;
  justify-content: space-around;
  margin-left: 350px;
}
</style>
