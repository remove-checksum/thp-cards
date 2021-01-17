<template>
  <div id="app" class="app app__wrapper">
    <Page :users="this.users"/>
    <Pagination @fetchPage="fetchPage" :pagesLimit="unpaginatedLength" :cardsPerPage="pageSize"/>
    <!-- <div v-for="user in "> {{}} </div> -->
    <!-- <div v-for="user in users" :key="user.id">{{ user.id }}</div>
    <div 
      v-for="user of users"
      :key="user.id">
      <div>
        {{ user.last_name }}
      </div>
      <div>
        {{ user.first_name }}
      </div>
    </div> -->
  </div>
</template>

<script>
import Pagination from '@/components/Pagination.vue'
import Page from '@/components/Page.vue'

export default {
  name: 'App',
  components: {
    Page,
    Pagination
  },

  data() {
    return {
      users: null,
      unpaginatedLength: null,
      currentPage: 1,
      pageSize: 9 // TODO: component to change this
    };
  },

  computed: {
  },

  methods: {
    fetchPage(page = 1) {
      let pageUrl = 'http://localhost:3001/?page=';
      
      console.log(`${pageUrl}${page}`);

      fetch(`${pageUrl}${page}`)
        .then((res) => res.json())
        .then((data) => {
          (this.users = data.payload);
          (this.unpaginatedLength = data.limit);
        });
    }
  },
  
  mounted() {
    fetch('http://localhost:3001/')
      .then((res) => res.json())
      .then((data) => {
          (this.users = data.payload);
          (this.unpaginatedLength = data.limit);
        });
  }
}
</script>

<style lang="scss">
@import '~normalize.css';

*,
*::before,
*::after {
  box-sizing: border-box;
}

li {
  list-style-type: none;
}

.app { 
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 40px;

  &__wrapper {
    width: 50%;
    margin: 0 auto;
  }
}
</style>
