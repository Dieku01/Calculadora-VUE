<template>
  <div id="app">
    <header>
      <span>PWA - Calculadora - Vuejs</span>
    </header>
    <main>
      <calculadora></calculadora>
    </main>
  </div>
</template>

<script>
import Calculadora from "./components/Calculadora.vue";

export default {
  name: "App",
  components: {
    Calculadora
  }
};
</script>

<style>
body {
  margin: 0;
  background-color: black;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  text-align: center;
  width: 90%;
  max-width: 400px;
  margin-top: 40px;
  margin-left: auto;
  margin-right: auto;
}

header {
  margin: 0;
  height: 56px;
  padding: 0 16px 0 24px;
  background-color: #35495e;
  color: #ffffff;
  text-align: center;
}

header span {
  display: block;
  position: relative;
  font-size: 20px;
  line-height: 1;
  letter-spacing: 0.02em;
  font-weight: 400;
  box-sizing: border-box;
  padding-top: 16px;
}
</style>
