<template>
  <div class="days">
    <table>
      <thead>
        <tr>
          <th>Mon</th>
          <th>Tue</th>
          <th>Wed</th>
          <th>Thu</th>
          <th>Fri</th>
          <th>Sat</th>
          <th>Sun</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(week, i) in getWeeks.length" :key="i">
          <td v-for="(day, j) in getWeeks[week-1]" :key="j">{{day}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Days',
  props: {
    currentYear: Number,
    currentMonth: Number
  },
  computed: {
    getWeeks() {
      const month = this.currentMonth+1;
      const firstDay = new Date(`${this.currentYear}-${month}-01`).getDay();
      const daysInCurrentMonth = new Date(this.currentMonth, month, 0).getDate();
      let days = [];

      //add '0' before start month to array
      if(firstDay === 1) {
        return;
      } else if (firstDay === 0) {
        for(let i = 0; i <= 6; i++) {
          days.push(0);
        }
      } else {
        for(let i = 0; i < firstDay - 1; i++) {
          days.push(0);
        }
      }

      //add days in month to array
      for(let i = 1; i <= daysInCurrentMonth; i++) {
        days.push(i);
      }

      //add '0' after end month to array
      const number = 7 - (days.length % 7)
      for(let i = 0; i < number; i++) {
        days.push(0);
      }

      //split days to weeks
      let weeks = []
      let chunk = 7;
      for (let i = 0; i < days.length; i+=chunk) {
        const week = days.slice(i, i+chunk);
        weeks.push(week);
      }

      return weeks;
    }
  }
}
</script>

<style lang="sass">

</style>