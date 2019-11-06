<template>
  <article id="Result">
    <button id="result-button" @search="searchTerm(result)">
      <img id="dino-egg" src="../assets/egg.svg"/>
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
      this.term = result
      this.$emit("search", result);
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
    border: none;
    background-color: transparent;
    width: 60%;
    height: 210px;
    color: black;
    position: relative;
    text-align: center;
    border-radius: 100%;
    margin-bottom: 50px;
  }

  #dino-egg {
    height: 200px;
  }

  #result-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-weight: bold;
    font-size: 15px;
  }

</style>