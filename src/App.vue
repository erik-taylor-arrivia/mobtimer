<template>
  <div id="app">
    <!-- <HelloWorld msg="The NPM MobTimer"/> -->
    <MobTimer />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import MobTimer from './components/MobTimer.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    MobTimer
  }
}
</script>

<style lang="scss">
body {
  background-image: url('./assets/mobsters.jpg');
  height: 85vh;
  margin: 0;
  -webkit-font-smoothing: auto;
  -moz-osx-font-smoothing: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-family: Roboto, sans-serif;
  background-repeat: no-repeat;
  background-position: 66% 0%;

    @media (max-width: 768px) {
        background-position: 96% 0%;
    }

}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 auto 5em;
  padding: 1em;
  max-width: 20%;
  background-color: #fff;
  border-radius: 6px;
}
</style>
