<template>
  <div id="app">
    <Header title="Ynte's Vue To-Do App"/>
    <AddTask />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import AddTask from './components/AddTask.vue';


export default {
  name: 'App',
  components: {
    Header,
    AddTask
  }
}
</script>

<style>
#app {
  font-family: Arial, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 100px;
}
</style>
