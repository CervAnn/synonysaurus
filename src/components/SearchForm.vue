<template>
  <main>
    <section id="SearchContainer">
      <form id="SearchForm" @submit.prevent="searchTerm(term)">
        <h1 id="search-prompt">Search Term</h1>
        <div id="search-submit-container">
          <input id="search-input" type="text" placeholder="Enter search term..." v-model="term"/>
          <button id="submit-button" type="submit" @click="searchTerm(term)" :disabled="term ? false : true">
            <img id="volcano" src='../assets/volcano.svg'/>
            <p id="search-text">Get Synonyms!</p>
          </button>
        </div>
      </form>
    </section>
    <h1 id="error-message" v-if="results.length === 0 && error">We're unable to find synonyms for this word. Please try searching a different term.</h1>
    <h1 id="search-suggest" v-else-if="results.length === 0 && !error">Please Enter a Search Term to Get Synonyms...</h1>
    <h1 id="searched-term" v-else>Displaying {{results.length}} Synonyms for "{{ display }}"...</h1>
    <section id="ResultsContainer">
    <Result v-for="(result, index) in results" :key="index" :result="result" @search="searchTerm(result)" :display="display"/>
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
  data() {
    return {
      term: "",
      display: "", 
      results: [],
      error: ""
    }
  },
  methods: {
    searchTerm(term) {
      this.display = term
      const url = `https://dictionaryapi.com/api/v3/references/thesaurus/json/${term}?key=70844809-6b63-4d12-b44a-8f4ca91522b5`
      fetch(url)
      .then(this.results = [])
      .then(response => response.json())
      .then(data => data === undefined ? this.results = [] : this.results = data[0].meta.syns[0])
      .catch(error => this.error = error)
      this.term = ""
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

#search-suggest, #searched-term, #error-message {
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