<template>
  <div id="page">
    <Grid />
    <Pagination />
  </div>
</template>

<script>
import Pagination from '@/components/Pagination.vue'
import Grid from '@/components/Grid.vue'

export default {
  name: 'Page',
  components: {
    Grid,
    Pagination
  }
}
</script>