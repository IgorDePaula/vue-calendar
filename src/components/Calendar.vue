<template>
   <div>
     <div>
       <button @click="view = 'Day'">Dia</button>
       <button @click="view = 'Week'">Semana</button>
       <button @click="view = 'Month'">Mes</button>
     </div>
     <h2></h2>
     <component :events="events" :locale="locale" :formatDate="formatDate" :is="view"></component>
   </div>
</template>

<script>
import moment from 'moment'
import Day from './Day'
import Month from './Month'
import Week from './Week'
export default {
  name: 'Calendar',
  components: {
    Day, Month, Week
  },
  props: {
    formatDate: {
      required: true,
      type: String
    },
    locale: {
      type: String,
      default: () => 'pt-br'
    },
    events: {
      required: true,
      type: Array
    }
  },
  computed: {
    getDateFromFormat () {
      return moment().format(this.formatDate)
    }
  },
  created () {
    moment().locale(this.locale)
  },
  data () {
    return {
      view: 'Day',
      moment: moment().locale(this.locale)
    }
  }
}
</script>

<style scoped>
</style>
