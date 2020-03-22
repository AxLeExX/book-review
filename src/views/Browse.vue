<template>
<div class="pure-menu pure-menu-horizontal">
  <ul class="pure-menu-list">
    <li class="pure-menu-item"><a @click="select('Title')" href="#" class="pure-menu-link">Title</a></li>
    <li class="pure-menu-item"><a @click="select('Author')" href="#" class="pure-menu-link">Author</a></li>
    <li class="pure-menu-item"><a @click="select('Rating')" href="#" class="pure-menu-link">Rating</a></li>
    <li class="pure-menu-item"><a @click="select('ISBN')" href="#" class="pure-menu-link">ISBN</a></li>
  </ul>
</div>
<div class="search">
  <form class="pure-form">
    <i class="fas fa-search"></i><input v-model="searchText" />
  </form>
</div>
</template>


<script>
import BookList from "../components/BookList.vue"
export default {
  name: 'Browse'
  components: {
    BookList
  },
  data() {
    return {
      searchType: '',
      searchText: '',
    }
  },
  computed: {
    books() {
        if(this.searchType == 'Title') {
          return this.$root.$data.books.filter(book => book.title.toLowerCase().search(this.searchText) >= 0);
        }
        else if(this.searchType == 'Author') {
          return this.$root.$data.books.filter(book => book.author_last_name.toLowerCase().search(this.searchText) && book.author_first_name.toLowerCase().search(this.searchText) >= 0);
        }
        else if(this.searchType == 'Rating') {
          return this.$root.$data.books.filter(book => book.average_rating.search(this.searchText) >= 0);
        }
        else if(this.searchType == 'ISBN') {
          return this.$root.$data.books.filter(book => book.isbn.search(this.searchText) >= 0);
        }
      }
  },
  methods: {
    select(type) {
      this.searchType = type;
    }
  }
}
</script>


<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.search {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 50%;
}

form {
  display: table;
  width: 100%;
}

i {
  display: table-cell;
  padding-left: 10px;
  width: 1px;
}

input {
  display: table-cell;
  font-size: 20px;
  border: none !important;
  box-shadow: none !important;
  width: 100%;
  height: 40px;
}
</style>
