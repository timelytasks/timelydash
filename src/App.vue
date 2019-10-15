<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Tasks v-bind:tasks="tasks"></Tasks>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Tasks from './components/Tasks';
export default {
  name: 'app',
  components: {
    Tasks
    // HelloWorld
  },
  data() {
    return {
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
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
