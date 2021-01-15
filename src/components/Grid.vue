<template>
  <div id="grid">
    <Card v-for="card of cards"/>
  </div>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
  name: 'Grid',
  components: {
    Card
  },
  props: ['cards']
}
</script>

<style lang="scss">
#grid {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
</style>