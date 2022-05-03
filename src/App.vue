<template>
  <div id="app">
    <h1>Problema de Monty Hall</h1>
    <p>O</p>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat");
* {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

html,
body {
  height: 100%;
}

body {
  color: #eee;
  background: #1a2980; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to bottom,
    #26d0ce,
    #1a2980
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to bottom,
    #26d0ce,
    #1a2980
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app h1 {
  border: 1px solid #fff;
  background-color: #fff2;
  padding: 0.5rem;
  margin: 1.5rem 0 4rem 0;
}
</style>
