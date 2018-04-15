<template>
    <div class="event">{{event.title}}</div>
</template>

<script>
export default {
  name: 'Event',
  props: {
    event: {
      required: true,
      type: Object
    }
  },
  mounted () {
    console.log(this.event)
  }
}
</script>

<style scoped>

</style>
