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
    width: 25%;
    text-align: center;
  }

  button {
    border: none;
    background-color: transparent;
    width: 75%;
    margin: auto;
    height: 215px;
    color: black;
    position: relative;
    border-radius: 75%;
  }

  button:hover {
    background-color: #248b40;
  }

  #dino-egg {
    height: 200px;
    text-align: center;
  }

  #result-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-weight: bold;
    font-size: 15px;
    text-align: center;
  }

</style>