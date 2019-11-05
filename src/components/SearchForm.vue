<template>
  <main>
    <section id="SearchContainer">
      <form id="SearchForm" @submit.prevent="searchTerm">
        <h1 id="search-prompt">Search Term</h1>
        <div id="search-submit-container">
          <input id="search-input" type="text" placeholder="Enter search term..." v-model="term" required/>
          <button id="submit-button" type="submit" @click="searchTerm"><img id="volcano" src='../assets/volcano.svg'/></button>
        </div>
      </form>
    </section>
    <section id="ResultsContainer">
    <Result v-for="(result, index) in results" :key="index" :result="result" @search="searchTerm" :term="term"/>
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
      results: []
    }
  },
  methods: {
    searchTerm() {
      const url = `https://dictionaryapi.com/api/v3/references/thesaurus/json/${this.term}?key=70844809-6b63-4d12-b44a-8f4ca91522b5`
      fetch(url)
      .then(response => response.json())
      .then(data => this.results = data[0].meta.syns[0])
      .catch(error => console.log(error))
    }
  }
}
</script>

<style scoped>

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
}

#search-input {
  height: 40px;
  width: 100%;
  border-radius: 10px 0px 0px 10px;
  font-size: 20px;
  padding: 10px;
}

#ResultsContainer {
  height: 55vh;
  width: 100%;
  background-color: #E1A953;
  display: flex;
  flex-flow: row wrap;
}

#submit-button {
  background: transparent;
}

#submit-button:hover {
  background-color: yellow;
}

#volcano {
  height: 35px;
}
</style>