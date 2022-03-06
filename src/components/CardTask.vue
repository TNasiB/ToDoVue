<template>
<div class="task">
    <div class="task-bar">
        <div class="task-left">
            <p>{{ task.title }}</p>
            <button class="task-show"></button>
        </div>
        <div class="task-right">
            <button class="done-task">Done!</button>
            <button v-on:click="removeTask" class="remove-task"></button>
        </div>
    </div>
    <ul class="task-side">
        <li>{{ task.desc }}</li>
    </ul>
</div>
</template>

<script>
    export default {
        name: 'CardTask',
        props: ['task'],
        methods: {
            removeTask: function (e) {
                e.target.parentElement.parentElement.parentElement.remove()
                // this.$emit('remove-task', {

                // });
            }
        }
    }

</script>

<style>
.task {
    box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
    margin: 7px 0;
    padding: 7px 25px;
}
.task-bar {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}
.task-side {
    margin-left: 15px;
    text-align: left;
    margin-top: 7px;
    font-size: 14px;
}
.task-left {
    display: flex;
    flex-direction: row;
    align-items: center;
}
.task-show {
    background: url(../assets/show.svg) no-repeat;
    background-size: contain;
    height: 16px;
    width: 16px;
    border: none;
    background-color: transparent;
    margin-left: 7px;
}
.task-right {
    align-items: center;
    display: flex;
}
.done-task {
    background: rgba(24, 160, 251, 0.7);
    border: none;
    border-radius: 5px;
    padding: 4px 14px;
    color: #fff;
    font-weight: 700;
    box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
}
.remove-task {
    background: url(../assets/close.svg) no-repeat;
    background-size: 12px;
    background-position: center;
    border: none;
    background-color: transparent;
    margin-left: 7px;
    padding: 15px;
    border-radius: 50%;
}
.remove-task:hover {
    background-color: rgba(221, 75, 57, 0.7);;
}
</style>