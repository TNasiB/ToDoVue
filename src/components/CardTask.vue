<template>
<div class="tasks">
    <div class="task">
        <p class="tasks-title">NEED TO DO</p>
        <button class="filter-btn"></button>
        <p>{{ task.title }}</p>
        <p>{{ task.desc }}</p>
    </div>
</div>
</template>

<script>
    export default {
        name: 'CardTask',
        props: ['task'] 
    }
</script>

<style>

</style>