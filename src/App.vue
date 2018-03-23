<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <Input/>
    <Tab/>
    <ToDoList/>
    <Pageation/>
    <Checkbox/>
    <LayOut/>
    <Search/>
    <Switchs/>
    <Toast/>
  </div>
</template>

<script>
  import HelloWorld from './components/HelloWorld'
  import Input from './components/Input'
  import Tab from './components/Tab'
  import ToDoList from './components/ToDoList'
  import Pageation from './components/Pageation'
  import Checkbox from './components/Checkbox'
  import LayOut from './components/LayOut'
  import Search from './components/Search'
  import Switchs from './components/Switchs'
  import Toast from './components/Toast'

  export default {
    name: 'App',
    components: {
      HelloWorld,
      Input,
      Tab,
      ToDoList,
      Pageation,
      Checkbox,
      LayOut,
      Search,
      Switchs,
      Toast,
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
