<template>
  <div class="days">
    <table class="days__table">
      <thead class="days__head">
        <tr class="days__weeks-name">
          <th class="days__week-name">Mon</th>
          <th class="days__week-name">Tue</th>
          <th class="days__week-name">Wed</th>
          <th class="days__week-name">Thu</th>
          <th class="days__week-name">Fri</th>
          <th class="days__week-name">Sat</th>
          <th class="days__week-name">Sun</th>
        </tr>
      </thead>
      <tbody class="days__body">
        <tr class="days__items" v-for="(week, i) in getWeeks.length" :key="i">
          <td
            class="days__item"
            v-for="(day, j) in getWeeks[week-1]" :key="j"
            v-bind:class="{'is-active': day === currentDate}"
          >
            {{day}}
          </td>
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
    currentMonth: Number,
    currentDate: Number
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
          days.push('');
        }
      } else {
        for(let i = 0; i < firstDay - 1; i++) {
          days.push('');
        }
      }

      //add days in month to array
      for(let i = 1; i <= daysInCurrentMonth; i++) {
        days.push(i);
      }

      //add '0' after end month to array
      const number = 7 - (days.length % 7)
      for(let i = 0; i < number; i++) {
        days.push('');
      }

      //split days to weeks
      let weeks = []
      let chunk = 7;
      for (let i = 0; i < days.length; i+=chunk) {
        const week = days.slice(i, i+chunk);
        weeks.push(week);
      }

      console.log(this.currentDate)

      return weeks;
    }
  }
}
</script>

<style lang="sass">
.days
  &__table
    margin: 0 auto
  &__week-name,
  &__item
    padding: 20px
    text-align: center
    text-transform: uppercase
    border: 1px solid tomato

  &__item
    font-size: 20px
    cursor: pointer
    transition: background-color 300ms
    &:hover
      background-color: rgba(255, 99, 71, 0.3)

    &.is-active
      background-color: rgba(255, 99, 71, 0.7)
</style>