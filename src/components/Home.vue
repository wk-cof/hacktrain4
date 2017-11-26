<template>
  <div class="bg-inverse text-white my-home-div">
    <dashboard class="my-db"></dashboard>
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
