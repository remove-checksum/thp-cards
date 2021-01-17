<template>
  <div class="page">
    <Card
      v-for="user of users"
      :key="user.id"
      :userpic="user.avatar"
      :fname="user.first_name"
      :lname="user.last_name"
      @click="fetchUserg ">
    </Card>
  </div>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
  name: 'Page',
  components: {
    Card
  },
  props: ['users'],
}
</script>

<style lang="scss">
// .page {
//   width: 80%;
//   max-width: 1280px;
//   margin: 0 auto;
//   padding: 1em;

//   display: grid;
//   grid-template-columns: 1fr 1fr 1fr;
//   grid-template-rows: auto;
//   grid-gap: 1em;

//   background-color: #7febba;
// }

.page {
  display: flex;
  flex-flow: row wrap;
  justify-content: flex-start;
  
  width: 860px;
  min-height: 770px;
  margin: 0 auto;
  padding: 20px;
  
  gap: 5px;

  background-color: #7febba;
 }
</style>