<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Header/>
    <AddTask/>
    <Tasks v-bind:tasks="tasks" v-on:del-task="deleteTask"/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Tasks from './components/Tasks';
import AddTask from './components/AddTask';


export default {
  name: 'app',
  components: {
    Header,
    Tasks,
    AddTask,

  },
  data() {
    return {
      // GET 
      tasks: [
          {
              "id": 1,
              "title": "Finish this project",
              "description": "Finish this goddamned project fast!",
              "completed": false,
              "created": "2019-10-10T22:45:44.578617Z",
              "url": "http://localhost:8000/api/v1/tasks/1/"
          },
          {
              "id": 2,
              "title": "Feed the cats",
              "description": "Don't let the cats die of hunger",
              "completed": false,
              "created": "2019-10-10T22:46:01.000749Z",
              "url": "http://localhost:8000/api/v1/tasks/2/"
          },
          {
              "id": 3,
              "title": "This task was done before I registered",
              "description": "So why did I register it?",
              "completed": true,
              "created": "2019-10-10T23:18:29.067057Z",
              "url": "http://localhost:8000/api/v1/tasks/3/"
          }
      ]
    }
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
      // DELETE
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
