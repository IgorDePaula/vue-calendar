<template>
  <div>
    <div>Dia {{day}}</div>
    <line-day v-for="(ih, index) in listHours" :events="listEvents" :key="index" :label="ih"></line-day>
  </div>
</template>

<script>
import moment from 'moment'
import LineDay from './LineDay'
export default {
  name: 'Day',
  components: {
    LineDay
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
    day () {
      return this.moment.format(this.formatDate)
    },
    listEvents () {
      return this.events.map(item => {
        let obj = {}
        obj.start = moment(item.start).date()
        obj.end = moment(item.end).date()
        obj.title = item.title
        console.log(obj)
        return obj
      }).filter(item => {
        const day = moment().day()
        return item.start === day || item.end === day
      })
    }
  },
  mounted () {
    this.createListHours()
    console.log(this.listEvents)
  },
  methods: {
    createListHours () {
      const start = moment().set({hours: '00', minutes: '00'})
      const end = moment().set({hours: '23', minutes: '59'})
      // eslint-disable-next-line
      for (const interval = start; interval < end; interval.add({minutes: 30})) {
        this.listHours.push({h: interval.format('HH'), m: interval.format('mm')})
      }
    }
  },
  data () {
    return {
      moment: moment().locale(this.locale),
      listHours: []
    }
  }
}
</script>

<style scoped>
</style>
