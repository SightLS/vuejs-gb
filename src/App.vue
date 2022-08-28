<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <CalcSum/>
  </div>

</template>

<script>
import CalcSum from '@/components/CalcSum'
export default {
  name: 'App',
  components: {
    CalcSum
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
