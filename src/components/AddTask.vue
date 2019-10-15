<template>
    <div>
        <form v-on:submit="addTask">
            <input type="text" v-model="title" name="title" placeholder="Add task">
            <input type="submit" value="Submit" class="btn">
            <!-- <button type="button" class="btn">Submit</button> -->
        </form>
    </div>
</template>

<script>
import axios from 'axios'


export default {
    name: "AddTask",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTask() {
            const newTask = {
                title: this.title,
                description: null,
                completed: false
            }
            // Send up to parent
            this.$emit('add-task', newTask);
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }
</style>