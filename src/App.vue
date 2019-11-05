<template>
  <div id="app">
    <SearchForm />
  </div>
</template>

<script>
import SearchForm from './components/SearchForm'

export default {
  name: 'app',
  components: {
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
