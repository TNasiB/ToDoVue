<template>
    <div class="new-task">
        <p class="input-name">Todo list on Vue.js</p>
        <p class="title-name">Title</p>

        <input type="text" class="task-title" v-on:keyup.enter="addTask">

        <span class="validation hide">Please, enter title of task</span>
        <p class="desc-name">Description</p>

        <input type="text" class="task-desc" v-on:keyup.enter="addTask">

        <button 
        v-on:click="addTask()" 
        class="add-task"
        >Add task
        </button>

        <button
        v-on:click="removeAllTasks" 
        class="remove-tasks"
        >Remove all tasks</button>

    </div>
</template>

<script>
    export default { 
        name: 'AddTask',
        methods: {
            addTask() {
                let title = document.querySelector(".task-title"),
                    desc = document.querySelector(".task-desc"),
                    validation = document.querySelector(".validation")
                if (title.value == "") {
                    title.style.border = "1px solid red"
                    validation.classList.remove("hide")
                    //Проверка не пустой ли инпут
                } else {
                    title.style.border = "1px solid transparent"
                    validation.classList.add("hide")
                    this.$emit('add-task', {
                    title: title.value,
                    desc: desc.value,
                    isCompleted: false, //Инициализируем свойство завершенности задачи, с помощью которой будем прописывать классы в css
                    date: new Date() //Инициализация свойства для сортировки по дате в дальнейшем
                    });
                }

                title.value = ""
                desc.value = ""
            },
            removeAllTasks() {
                this.$emit('delete-all-tasks')
            }
        }
    }
</script>

<style>
p {
    margin: 0;
}
.task-title {
    border: 1px solid transparent;
}
.validation {
    font-size: 14px;
    text-align: left;
    padding-left: 30px;
    margin-top: 5px;
    color: red;
}
.validation.hide {
    display: none;
}
.new-task {
    box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
    display: flex;
    flex-direction: column;
    width: 450px;
    margin: 0 auto;
    border-radius: 10px;
}
.input-name {
    background-color: #C4C4C44F;
    margin-top: 0;
    border-radius: 10px 10px 0 0;
    padding: 7px 0;
    color: #000;
    font-weight: 700;
}
.title-name, .desc-name {
    margin: 7px 0;
}
input {
    margin: 0 10px;
    border: none;
    box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
    border-radius: 5px;
    padding: 10px;
    outline: none;
    transition: border .2s;
}
.add-task, .remove-tasks {
    color: #fff;
    border: none;
    padding: 10px;
    font-weight: 700;
    cursor: pointer;
    transition: color .2s, background-color .2s, border .2s;
}
.add-task {
    margin-top: 12px;
    background-color: #18A0FBB2;
    border: 1px solid transparent
}
.add-task:hover {
    background-color: #fff;
    color: #18A0FBB2;
    border: 1px solid #18A0FBB2;
}
.remove-tasks {
    background-color: #DD4B39B2;
    border-radius: 0 0 10px 10px;
    border: 1px solid transparent
}
.remove-tasks:hover {
    color: #DD4B39B2;
    background-color: #fff;
    border: 1px solid #DD4B39B2;
}
</style>