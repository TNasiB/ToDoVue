<template>
  <div id="app">
    <AddTask @add-task="saveNewTask"></AddTask>
    <div class="cards-wrapper">
        <div class="need">
            <div class="need-title__wrapper">
                <span></span>
                <p class="need-title">NEED TO DO</p>
                <button class="filter-btn" ></button>
            </div>
            <div class="tasks-wrapper">
              <CardTask @remove-task="removeTask" v-for="(task, index) in tasks" :key="index" v-bind:task="task"></CardTask>
            </div>
        </div>
        <div class="done">
            <div class="done-title__wrapper">
                <span></span>
                <p class="need-title">DONE!</p>
                <button class="filter-btn"></button>
            </div>
        </div>   
    </div>
  </div>
</template>

<script>
  import AddTask from "./components/AddTask.vue";
  import CardTask from "./components/CardTask.vue";

  export default {
    name: 'App',
    data() {
        return {
            tasks : [],
        }
    },
    components: {
      AddTask,
      CardTask,
    },
    methods: {
      saveNewTask(data) {
        this.tasks.push(data)
      },
    }
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
* {
  padding: 0;
}
.cards-wrapper {
    width: 450px;
    margin: 0 auto;
    margin-top: 30px;
    border-radius: 10px;
    box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
}
.need + .done {
    margin-top: 10px;
}
.need-title__wrapper {
    background-color: #FFB229;
    border-radius: 10px 10px 0 0;
    color: #fff;
    font-weight: 700;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
    margin-top: 7px;
    padding: 8px;

}
.filter-btn {
    background-color: transparent;
    background: url("./assets/filter.svg") no-repeat;
    width: 24px;
    height: 24px;
    background-size: contain;
    border: none;
}
.done-title__wrapper {
    background: #4AD395;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
    padding: 8px;
    color: #fff;
    font-weight: 700;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
button {
  cursor: pointer;
}
</style>
