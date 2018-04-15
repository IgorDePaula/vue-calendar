<template>
  <div>
    <div>Semana {{week}}</div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  name: 'Week',
  props: {
    locale: {
      type: String,
      default: () => 'pt-br'
    }
  },
  computed: {
    week () {
      return this.moment.week()
    }
  },
  data () {
    return {
      moment: moment().locale(this.locale)
    }
  }
}
</script>

<style scoped>

</style>
