<template>
  <Logo />
  <TodoMain />
  <Footer />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Footer from "./components/Footer.vue";
import Logo from "./components/Logo.vue";
import TodoMain from "./components/TodoMain.vue";

@Options({
  components: {
    Logo,
    TodoMain,
    Footer,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
:root {
  --white: #efefef;
  --black: #363636;
  --signal: #ff654d;
  --grey: #d8d8d8;
  --ared: #ff605c;
  --ayellow: #ffbd44;
  --agreen: #00ca4dae;
}

* {
  box-sizing: border-box;
  scroll-behavior: smooth;
  background-color: var(--black);
  font-size: 62.5%;
  -ms-overflow-style: -ms-autohiding-scrollbar;
}

body {
  overflow: auto;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--black);
  background-color: var(--black);
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
