<template>
  <div id="app">
    <Month :month="new Date().getMonth()" :year="new Date().getFullYear()"/>
    <Days
      :currentDate="new Date().getDate()"
      :currentMonth="new Date().getMonth()"
      :currentYear="new Date().getFullYear()"
    />
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

<style lang="sass">
body
  font-family: Avenir, Helvetica, Arial, sans-serif
  color: #2c3e50

// html,
// body,
// p
//   margin: 0
//   padding: 0

</style>
