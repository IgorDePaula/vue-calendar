<template>
  <div id="app">
    <calendar :events="events" formatDate="L" locale="pt-br"></calendar>
  </div>
</template>

<script>
import Calendar from './components/Calendar'
export default {
  name: 'App',
  components: {
    Calendar
  },
  data () {
    return {
      events: [
        {
          start: '2018-04-15T18:31:21.178Z',
          end: '2018-04-15T19:31:21.178Z',
          title: 'event 1'
        },
        {
          start: '2018-04-15T12:31:21.178Z',
          end: '2018-04-15T13:31:21.178Z',
          title: 'event 2'
        }
      ]
    }
  }
}
</script>

<style>
  .label{
    font-size: 12px;
  }
  .event{
    background-color: aqua;
  }
</style>
