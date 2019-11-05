<template>
  <article id="Result">
    <button id="result-button" @search="searchTerm(result)">
      <p id="result-text">{{result}}</p>
    </button>
  </article>
</template>

<script>

export default {
  name: "Result",
  props: ['result'],
  methods: {
    searchTerm(result) {
      this.$emit("search", result.result);
    }
  }
}
</script>

<style scoped>
  #Result {
    height: 100px;
    width: 25%;
  }

  button {
    background: none;
    width: 100%;
    height: 100%;
    color: black;
  }

</style>