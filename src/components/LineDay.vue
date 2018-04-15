<template>
  <div class="half">
    <div class="label">{{showLabel}}</div>
    <event v-for="(item, index) in getEvents" :key="index" :event="item"></event>
  </div>
</template>

<script>
import Event from './Event'
import moment from 'moment'
export default {
  name: 'LineDay',
  components: {
    Event
  },
  props: {
    label: {
      required: true,
      type: Object
    },
    events: {
      required: true,
      type: Array
    }
  },
  computed: {
    showLabel () {
      return `${this.label.h}:${this.label.m}`
    }
  },
  methods: {
    getEvents () {
      return this.events.filter(item => {
        return moment(item.start).hour() === this.label.h || moment(item.end).hour() === this.label.h
      })
    }
  }
}
</script>

<style scoped>
  .label {
    width: 20%;
    height: 20%;
    border: 1px solid yellow;
    float: left;
  }

  .half {
    width: 99%;
    height: 50px;
    border: 1px solid red;
    float: left;
  }
</style>
