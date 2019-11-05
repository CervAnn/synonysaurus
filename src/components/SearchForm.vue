<template>
  <form id="SearchForm" @submit.prevent="searchTerm">
    <h1>Search Term</h1>
    <input type="text" placeholder="Enter search term..." v-model="term" />
    <button type="submit" v-on:click="searchTerm">Submit</button>
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
  methods: {
    searchTerm() {
      const url = `https://dictionaryapi.com/api/v3/references/thesaurus/json/${this.term}?key=70844809-6b63-4d12-b44a-8f4ca91522b5`
      fetch(url)
      .then(response => response.json())
      .then(data => console.log(data))
    }
  }
}
</script>

<style scoped>
</style>