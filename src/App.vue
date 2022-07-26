<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <button style="width: 100px; height: 500px"  @click="install"> Install </button>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
       installEvent: undefined,
    };
  },
  beforeMount() {
    window.addEventListener('beforeinstallprompt', (e) => {
      e.preventDefault()
      this.installEvent = e
    })
  },
   methods: {
    dismiss() {
      this.installEvent = null;
    },
    install() {
        this.installEvent.prompt()
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
