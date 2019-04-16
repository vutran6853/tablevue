<template>
  <div id="app">
    <ShowRow/>
  </div>
</template>

<script>
import ShowRow from './components/ShowRow';

export default {
  name: 'app',
  components: {
    ShowRow
  }
}
</script>

<style>

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
