<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
    <tableView></tableView>
  </div>
</template>

<script>
  import TableView from './components/tableView/tableView'

  export default {
    components: {TableView},
    name: 'app'
  }
</script>

<style lang='scss'>

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  @import 'assets/styles';

</style>
