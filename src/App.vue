<template>
  <div id="app">
    <MobTimer />
    <MobForm />
  </div>
</template>

<script>
import MobTimer from './components/MobTimer.vue'
import MobForm from './components/Mobbers.vue'

export default {
  name: 'App',
  components: {
    MobTimer,
    MobForm
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
  background-position: 76% 0%;
  background-size: auto;

    @media (min-width: 1700px) {
      background-size: cover;
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
  background-color: #fff;
  border-radius: 6px;
  max-width: 80%;

  @media (min-width: 768px) {
    max-width: 40%;
  }

  @media (min-width: 1200px) {
    max-width:30%;
  }
}
</style>
