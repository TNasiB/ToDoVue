<template>
  <div id="app">
    <AddTask 
    @add-task="saveNewTask"
    @delete-all-tasks="removeAllTasks"
    ></AddTask>
    <div class="cards-wrapper">
        <div class="need">
            <div class="need-title__wrapper">
                <div class="need-title-top">
                  <span></span>
                  <p class="need-title">TASKS</p>
                  <button class="filter-btn" v-on:click="sortByDate"></button>
                </div>
                <div class="need-search">

                  <input 
                  type="text" 
                  class="search-input" 
                  placeholder="Enter title of task for find it" 
                  v-on:keyup.enter="findTask">

                  <button class="search-btn" v-on:click="findTask"></button>
                </div>
            </div>
            <div class="tasks-wrapper">
              <CardTask
               v-for="(task, index) in tasks" 
               :key="index" 
               :task="task" 
               :index="index" 
               @remove-task="removeTask"
               @compleate-task="compleateTask(task)"
               >
              </CardTask>
            </div>
            <div class="completed-tasks">
              <CardTask
              v-for="(task, index) in completedTasks" 
              :key="index" 
              :task="task" 
              :index="index" 
              @compleate-task="compleateTask(task)"
              @remove-task="removeTask"
              ></CardTask>
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
            tasks: [],
            completedTasks: [],
            index: Number,
            order: Number,
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
      removeTask(data) {
        if (data.isCompleted) {
          this.completedTasks = this.completedTasks.filter(item => item !== data)
        } else {
          this.tasks = this.tasks.filter(item => item !== data)
        }
      },    
      compleateTask(task) {
        if (task.isCompleted) {
          this.tasks.push(task)
          this.completedTasks = this.completedTasks.filter(item => item !== task)
        } else {
          this.completedTasks.push(task)
          this.tasks = this.tasks.filter(item => item !== task)
        }
        task.isCompleted = !task.isCompleted
        console.log(task.isCompleted)
      },
      removeAllTasks() {
        this.tasks = []
      },
      findTask() {
        let query = document.querySelector(".search-input").value
        let generalTasks = this.tasks.concat(this.completedTasks)
        let neededTask = generalTasks.find(task => task.title == query)
        alert(`
        Search results
        Name of task:${neededTask.title}
        Description of task${neededTask.desc}
        ${neededTask.isCompleted ? 'Task completed' : 'Task active'}
        `)
      },
      sortByDate() {
        console.log(1)
      }
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
.done-task.doneBtn {
    background-color: green;
}
.done-task.doneBtn:hover {
    color: green;
    background-color: #fff;
}
.completedStyle {
    background-color: rgb(233, 233, 233);
}
.need-title-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.search-input {
  flex: 1 1 auto;
  margin: 0;
  border-radius: 5px 0 0 5px;
  box-shadow: none;
  outline: none;
}
.search-btn {
  width: 36px;
  height: 36px;
  border: none;
  background: rgba(24, 160, 251);
  border-radius: 0 5px 5px 0;
  border-left: 1px solid #00000059;
  background-image: url(./assets/search.png);
  background-size: 22px;
  background-repeat: no-repeat;
  background-position: center;
  transition: background .2s;
}
.search-btn:hover {
  background-color: rgb(80, 185, 255);
}
.need-search {
  display: flex;
  flex-direction: row;
  box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
  border-radius: 5px;
  border: 1px solid #00000059;
  margin-top: 10px;
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
    flex-direction: column;
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
