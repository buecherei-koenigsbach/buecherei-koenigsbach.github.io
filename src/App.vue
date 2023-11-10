<script setup>
import SearchSort from './components/SearchSort.vue';
import BookList from './components/BookList.vue';
</script>

<template>
  <div>
    <SearchSort @search="handleSearch" @sort="handleSort" />
    <BookList
      :books="filteredBooks"
      :currentPage="currentPage"
      :itemsPerPage="itemsPerPage"
      @pageChange="handlePageChange"
    />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

<script>
export default {
  data() {
    return {
      books: [],
      filteredBooks: [],
      currentPage: 1,
      itemsPerPage: 10,
    };
  },
  mounted() {
    this.fetchBooks();
  },
  methods: {
    async fetchBooks() {
      try {
        const response = await fetch('https://openlibrary.org/people/honnel/books/want-to-read.json');
        const data = await response.json();
        this.books = data.reading_log_entries.map(e => e.work);
        this.filteredBooks = this.books;
      } catch (error) {
        console.error('Error fetching books:', error);
      }
    },
    handlePageChange(page) {
      this.currentPage = page;
    },
    handleSearch(searchTerm) {
      // Implement search logic here
    },
    handleSort(sortBy) {
      // Implement sort logic here
    },
  },
  components: {
    SearchSort,
    BookList,
  },
};
</script>
