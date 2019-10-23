<template>
    <div class="task-item" v-bind:class="{'is-complete': task.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{ task.title }}
            <button v-on:click="$emit('del-task', task.id)"
                class="del">X</button>
        </p>
        <p>{{ task.description }}</p>
        <!-- <p>Created at: {{ task.created }}</p> -->
    </div>
</template>

<script>
export default {
    name: "TaskItem",
    props: ["task"],
    methods: {
        markComplete() {
            this.task.completed = !this.task.completed; 
        },
        // showTime() {
        //     this.task.created = moment(this.task.created).format('MMMM Do YYYY, h:mm:ss a')
        // }
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
    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 8px 12px;
        /* border-radius: 50%; */
        cursor: pointer;
        float: right;
    }
</style>