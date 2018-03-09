<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <Input/>
    <Tab/>
    <ToDoList/>
  </div>
</template>

<script>
  import HelloWorld from './components/HelloWorld'
  import Input from './components/Input'
  import Tab from './components/Tab'
  import ToDoList from './components/ToDoList'

  export default {
    name: 'App',
    components: {
      HelloWorld,
      Input,
      Tab,
      ToDoList
    }
  }
</script>
<style lang="scss" scoped>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    img {
      width: 30px;
      height: 30px;
    }
  }
</style>
