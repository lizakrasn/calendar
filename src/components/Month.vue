<template>
  <div class="month">
    <p class="month__name">{{ monthName }}</p>
  </div>
</template>

<script>
export default {
  name: 'Month',
  props: {
    month: Number,
    year: Number
  },
  computed: {
    monthName() {
      const months = ["January", "February", "March", "April", "May", "June",
    "July", "August", "September", "October", "November", "December"
      ];
      
      return `${months[this.month]}, ${this.year} year`
    }
  }
}
</script>

<style lang="sass">
.month
  display: flex
  justify-content: center
  font-size: 48px
  color: tomato
</style>