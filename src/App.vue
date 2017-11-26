<template>
  <div id="app">
    <nav class="navbar navbar-fixed-top navbar-toggleable-md navbar-inverse my-nav">
      <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <!-- <a class="navbar-brand" href="/">GeoIncident</a> -->
      <a class="navbar-brand" href="#">
        <img src="./assets/logo.png" width="30" height="30" alt="qwer">
        <span class="text-success">Geo-Incident</span>
      </a>
      <!-- <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <a class="nav-link" href="/about">All Stations</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/contact">Affected Stations</a>
          </li>
        </ul>
      </div> -->
    </nav>
    <div class="container-fluid">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: 'delay-sim'
    }
  },
  components: {
  }
}
</script>

<style>
  input:focus,
  select:focus,
  textarea:focus,
  button:focus {
    outline: none;
  }

  .navbar { margin-bottom: 50px; }
  /* .my-nav {
    background: #ffffff;
  } */
  p {
    margin: 0em;
  }

  p.lead {
    font-weight: 500;
    margin-bottom: 1em;
    color: #888;
  }

  h1, h2 {
    font-weight: 900;
    margin-bottom: 1em;
  }

  h3, h4 {
    margin-top: 1em;
    font-weight: 700;
    margin-bottom: 1em;
  }
</style>
