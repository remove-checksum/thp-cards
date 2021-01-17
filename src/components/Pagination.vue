<template>
    <ul class="pagination">
      <li>
        <button
          ref="prev" 
          @click="changePage(currentPage - 1)"
          class="pagination__button pagination__button--left"
          :disabled="isBorder() === 'start'"
        >&lt;</button>
      </li>
      <li
        v-for="btn in paginatorButtons"
        :key="btn"
      >
        <button
          @click="changePage(btn)"
          class="pagination__button pagination__button--numbered"
          :class="{ active: isCurrent(btn) }"
          :disabled="isCurrent(btn)"
        >
        {{btn}}
        </button>
      </li>
      <li>
        <button
          ref="next"
          @click="changePage(currentPage + 1)"
          class="pagination__button pagination__button--right"
          :disabled="isBorder() === 'end'"
        >&gt;</button>
      </li>
    </ul>
</template>

<script>

export default {
  name: 'Pagination',
  props: {
    pagesLimit: {
      type: Number,
      required: true
    },
    cardsPerPage: {
      type: Number,
      required: true
    }
  },
  
  data() {
    return {
      currentPage: 1,
      visibleButtons: 4
    }
  },

  computed: {
    numberOfPages() {
      return Math.ceil(this.pagesLimit / this.cardsPerPage);
    },
    pagesRange() {
      return Array.from({ length: this.numberOfPages }, (l, u) => u + 1);
    },
    paginatorButtons () {
      return this.pagesRange.slice(this.currentPage - 1, this.currentPage - 1 + this.visibleButtons);
    },
  },

  methods: {
    changePage(page) {
      this.$emit('fetchPage', page);
      this.currentPage = page;
    },
    isCurrent(currentPageIndex) {
      return currentPageIndex === this.currentPage;
    },
      isBorder() {
        if (this.currentPage === 1) return 'start';
        if (this.currentPage === this.numberOfPages) return 'end';
      }
  },
}
</script>

<style lang="scss">
.pagination {
  display: flex;
  flex-grow: 1;
  max-width: 60%;

  margin: 0 auto;
  padding: 10px 0;
  justify-content: space-between;
  align-items: center;

  &__button--left {
    margin-right: 50px;
  }

  &__button--right {
    margin-left: 50px;
  }
}

.active {
  color: #42b983;
}
</style>