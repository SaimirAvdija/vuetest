<template>
<div>
  {{valveInfo}}
  {{pumpInfo}}
  {{tankInfo}}
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data () {
    return {
      valveInfo: null,
      pumpInfo: null,
      tankInfo: null
    }
  },
 mounted () {
    axios.get('https://localhost:44374/api/vrc/GetAllValves')
      .then(response => (this.valveInfo = response.data));
    axios.get('https://localhost:44374/api/vrc/GetAllPumps')
      .then(response => (this.pumpInfo = response.data));
    axios.get('https://localhost:44374/api/vrc/GetAllTanks')
      .then(response => (this.tankInfo = response.data));
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>