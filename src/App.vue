<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Header/>
    <AddTask v-on:add-task="addTask"/>
    <Tasks v-bind:tasks="tasks" v-on:del-task="deleteTask"/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Tasks from './components/Tasks';
import AddTask from './components/AddTask';
import axios from 'axios'


export default {
  name: 'app',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    async deleteTask(id) {
      try {
        let response = await axios.delete('http://localhost:8000/api/v1/tasks/' + id);
        console.log(response)
      } catch(e) {
        console.error(e)
      }
    },
    async addTask(newTask) {
      console.log(newTask)
      try {
        let response = await axios.post('http://localhost:8000/api/v1/tasks/', newTask);
        console.log(response)
        this.tasks = response.data;
      } catch(e) {
        console.error(e)
      }
    }
  },
  async created() {
    try {
      let response = await axios.get('http://localhost:8000/api/v1/tasks/');
      console.log(response)
      this.tasks = response.data;
    } catch(e) {
      console.error(e)
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>
