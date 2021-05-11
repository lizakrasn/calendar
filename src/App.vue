<template>
  <div id="app">
    <Month :month="new Date().getMonth()" :year="new Date().getFullYear()"/>
    <Days :currentMonth="new Date().getMonth()" :currentYear="new Date().getFullYear()"/>
  </div>
</template>

<script>
import Month from './components/Month.vue';
import Days from './components/Days.vue'

export default {
  name: 'App',
  components: {
    Month,
    Days
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
