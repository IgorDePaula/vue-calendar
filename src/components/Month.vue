<template>
  <div>
    <div>Mes {{month}}</div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  name: 'Month',
  props: {
    locale: {
      type: String,
      default: () => 'pt-br'
    }
  },
  data () {
    return {
      moment: moment().locale(this.locale)
    }
  },
  computed: {
    month () {
      return this.moment.format('MMMM')
    }
  }
}
</script>

<style scoped>

</style>
