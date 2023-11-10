<template>
    <div>
      <div v-for="book in paginatedBooks" :key="book.key">
        <h2>{{ book.title }}</h2>
        <p>Author: {{ book.author_names.join(', ') }}</p>
        <p>Year: {{ book.first_publish_year }}</p>
        <img :src="'http://covers.openlibrary.org/b/olid/' + book.cover_edition_key + '-M.jpg'">
     </div>
      <Pagination
        :totalPages="totalPages"
        :currentPage="currentPage"
        @pageChange="handlePageChange"
      />
    </div>
  </template>
  
  <script>
  export default {
    props: {
      books: Array,
      currentPage: Number,
      itemsPerPage: Number,
    },
    computed: {
      paginatedBooks() {
        const start = (this.currentPage - 1) * this.itemsPerPage;
        const end = start + this.itemsPerPage;
        return this.books.slice(start, end);
      },
      totalPages() {
        return Math.ceil(this.books.length / this.itemsPerPage);
      },
    },
    methods: {
      handlePageChange(page) {
        this.$emit('pageChange', page);
      },
    },
  };
  </script>
  