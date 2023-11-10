<template>
    <div>
      <button v-for="page in totalPages" :key="page" @click="changePage(page)">
        {{ page }}
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      totalPages: Number,
      currentPage: Number,
    },
    methods: {
      changePage(page) {
        this.$emit('pageChange', page);
      },
    },
  };
  </script>
  