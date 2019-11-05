<template>
  <div id="app">
    <Header />
    <SearchForm />
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
