<template>
  <form id="SearchForm">
    <h1>Search Term</h1>
    <input type="text" placeholder="Enter search term..." v-model="term" />
    <button type="submit" v-on:click="searchTerm(term)">Submit</button>
  </form>
</template>

<script>
export default {
  name: 'SearchForm',
  data() {
    return {
      term: ""
    }
  },
  // methods: {
  //   async searchTerm() {
  //     const url = "https://dictionaryapi.com/api/v3/references/thesaurus/json/"
  //     const key = "?key=70844809-6b63-4d12-b44a-8f4ca91522b5"
  //     fetch(url + `${term}` + key) {

  //     }
  //   }
  // }
  
}
</script>

<style scoped>
</style>