<template>
  <div id="app">
    <AddTask @add-task="saveNewTask"></AddTask>
    <CardTable></CardTable>
  </div>
</template>

<script>
  import AddTask from "./components/AddTask.vue";
  import CardTable from "./components/CardsTable.vue"

  export default {
    name: 'App',
    components: {
      AddTask,
      CardTable,
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
button {
  cursor: pointer;
}
</style>
