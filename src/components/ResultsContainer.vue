<template>
  <section id="ResultsContainer">
    // <Result v-for="result in results" />
  </section>
</template>

<script>

// import SearchForm from './SearchForm'
import Result from './Result'

export default {
name: "ResultsContainer",
props: ["results"],
components: {
Result
}
  
}
</script>

<style scoped>

</style>