<template>
  <div id="app">
    <Header />
    <SearchForm v-bind:results="results" @search="searchTerm"/>
  </div>
</template>

<script>
import Header from './components/Header'
import SearchForm from './components/SearchForm'

export default {
  name: 'app',
  components: {
    Header,
    SearchForm
  },
  data() {
    return {
      results: []
    }
  },
  methods: {
    searchTerm(term) {
      console.log("app", term)
      const url = `https://dictionaryapi.com/api/v3/references/thesaurus/json/${term}?key=70844809-6b63-4d12-b44a-8f4ca91522b5`
      fetch(url)
      .then(response => response.json())
      .then(data => this.results = data[0].meta.syns[0])
      .catch(error => console.log(error))
    }
  }
}
</script>

<style>
 * {
   box-sizing: border-box;
   margin: 0;
   padding: 0;
 }
</style>
