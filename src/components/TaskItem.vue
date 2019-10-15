<template>
    <div class="task-item" v-bind:class="{'is-complete': task.completed}">
        <h3><input type="checkbox" v-on:change="markComplete">{{ task.title }}</h3>
        <p>{{ task.description }}</p>
        <p>Created at: {{ task.created }}</p>
    </div>
</template>

<script>
export default {
    name: "TaskItem",
    props: ["task"],
    methods: {
        markComplete() {
            this.task.completed = !this.task.completed; 
        }
    }
}
</script>

<style scoped>
    .task-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }
</style>