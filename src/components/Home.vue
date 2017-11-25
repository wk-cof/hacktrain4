<template>
  <div class="bg-inverse text-white">
    <dashboard></dashboard>
    <uk-map></uk-map>
  </div>
</template>

<script>
import Dashboard from './Dashboard';
import UkMap from './UkMap';

export default {
  name: "home",
  data() {
    return {
    };
  },
  components: {
    'dashboard': Dashboard,
    'uk-map': UkMap
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
