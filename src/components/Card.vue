<template>
  <div class="card">
    <img class="card__userpic" :src="userpic" alt="user avatar">
    <h2 class="card__username">{{ fname }} {{ lname }}</h2>
  </div>  
</template>

<script>
export default {
  name: 'Card',

  props: ['userpic', 'fname', 'lname']
}
</script>

<style lang="scss">
.card {
  background-color: #42b983;
  flex: 0 0 270px;
  padding-top: 20px;
  height: 240px;

  &__userpic {
    max-width: 50%;
    height: auto;
    align-self: center;

    clip-path: circle();
    background-color: #cccccc;
  }

}
</style>