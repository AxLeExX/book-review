<template>
<div>
  <BookList :books="books" />
</div>
</template>


<script>
import BookList from "../components/BookList.vue"
export default {
  name: 'Home',
  components: {
    BookList
  },
  data() {
    return {
      searchText: '',
    }
  },
  computed: {
    books() {
      return this.$root.$data.books.filter(book => book.title.toLowerCase().search(this.searchText) >= 0);
      }
  },
}
</script>


<style scoped>

</style>
