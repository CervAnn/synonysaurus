<template>
  <main>
    <section id="SearchContainer">
      <form id="SearchForm" @submit.prevent="searchTerm(term)">
        <h1 id="search-prompt">Search Term</h1>
        <div id="search-submit-container">
          <input id="search-input" type="text" placeholder="Enter search term..." v-model="term" required/>
          <button id="submit-button" type="submit" @click="searchTerm(term)">
            <img id="volcano" src='../assets/volcano.svg'/>
            <p id="search-text">Get Synonyms!</p>
          </button>
        </div>
      </form>
    </section>
    <h1 id="search-suggest" v-if="results.length === 0">Please Enter a Search Term to Get Synonyms...</h1>
    <h1 id="searched-term" v-else>Displaying Synonyms for "{{term}}"...</h1>
    <section id="ResultsContainer">
    <Result v-for="(result, index) in results" :key="index" :result="result" @search="searchTerm(term)" :term="term"/>
    </section>
  </main>
</template>

<script>
import Result from './Result'

export default {
  name: 'SearchForm',
  components: {
    Result
  },
  props: ['results'],
  data() {
    return {
      term: ""
    }
  },
  methods: {
    searchTerm(term) {
      console.log("search", term)
      this.$emit('search', this.term)
    }
  }
}
</script>

<style scoped>

main {
  height: 100%
}

#SearchContainer {
  height: 30vh;
  width: 100%;
  background-color: #E1A953;
  display: flex;
}

#SearchForm {
  width: 50%;
  height: 200px;
  border: 2px solid black;
  border-radius: 10px;
  margin: auto;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  font-family: 'McLaren', cursive;
  background-color: #014b0d;
}

#search-prompt {
  font-size: 30px;
  color: #E1A953;
  text-shadow:
		-1px -1px 0 #000,
		1px -1px 0 #000,
		-1px 1px 0 #000,
		1px 1px 0 #000;
}

#search-submit-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

#search-input {
  height: 40px;
  width: 35%;
  border-radius: 10px 0px 0px 10px;
  font-size: 20px;
  padding: 10px;
}

#ResultsContainer {
  height: 100vh;
  width: 100%;
  background-color: #E1A953;
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
  align-items: center;
  overflow: scroll;
}

#submit-button {
  background: transparent;
  width: 25%;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

#submit-button:hover {
  background-color: #248b40
}

#volcano {
  height: 35px;
}

#search-text {
  color: #E1A953;
  text-shadow:
		-1px -1px 0 #000,
		1px -1px 0 #000,
		-1px 1px 0 #000,
		1px 1px 0 #000;
    font-size: 20px;
}

#search-suggest, #searched-term {
  font-family: 'McLaren', cursive;
  color: #62745D;
  background-color: #E1A953;
  text-shadow:
		-1px -1px 0 #000,
		1px -1px 0 #000,
		-1px 1px 0 #000,
		1px 1px 0 #000;
    font-size: 40px;
  text-align: center;
}

</style>