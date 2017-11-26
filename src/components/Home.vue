<template>
  <div class="bg-inverse text-white my-home-div">
    <dashboard class="my-db" v-on:showsmallmap="showIt"></dashboard>
    <nav class="navbar navbar-fixed-top navbar-toggleable-md navbar-inverse">
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <a class="nav-link" href="/ukmap">All Stations</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/contact">Affected Stations</a>
          </li>
        </ul>
      </div>
    </nav>
    <uk-map v-if="!showSmallMap"></uk-map>
    <event-map v-else></event-map>
  </div>
</template>

<script>
import Dashboard from './Dashboard';
import UkMap from './UkMap';
import EventMap from './EventMap';

export default {
  name: "home",
  data() {
    return {
      showSmallMap: false
    };
  },
  components: {
    'dashboard': Dashboard,
    'uk-map': UkMap,
    'event-map': EventMap
  },
  methods: {
    showIt() {
      this.showSmallMap = true;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home-nav {
  align-items: flex-start important;
}
.my-home-div {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.my-db {
  margin-bottom: 30px;
}
</style>
