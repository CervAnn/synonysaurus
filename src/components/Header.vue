<template>
  <article id="Header-container">
    <h1>Synonysaurus</h1>
    <img id="dino" src="../assets/diplodocus.svg"/>
  </article>
</template>

<style scoped>
#Header-container {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #62745D;
  height: 15vh;
  font-family: 'McLaren', cursive;
  color: #E1A953;
  text-shadow:
		-1px -1px 0 #000,
		1px -1px 0 #000,
		-1px 1px 0 #000,
		1px 1px 0 #000;
  font-size: 35px;
}

#dino {
margin-left: 20px;
height: 100px;
}
</style>