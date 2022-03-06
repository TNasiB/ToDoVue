<template>
    <div class="cards-wrapper">
        <div class="need">
            <div class="need-title__wrapper">
                <span></span>
                <p class="need-title">NEED TO DO</p>
                <button class="filter-btn" ></button>
            </div>
        <CardTask v-for="(task, index) in tasks" :key="index" :task="task"></CardTask>
        </div>
        <div class="done">
            <div class="done-title__wrapper">
                <span></span>
                <p class="need-title">DONE!</p>
                <button class="filter-btn"></button>
            </div>
        </div>
    </div>
</template>

<script>
import CardTask from "./CardTask.vue";


export default {
    name: 'CardsTable',
    components: {
        CardTask,
    },
    data() {
        return {
            tasks : [],
        }
    },
    methods: {
      saveNewTask(data) {
        this.tasks.push(data)
       }
    }
}
</script>

<style>
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
    background: url("../assets/filter.svg") no-repeat;
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
</style>
