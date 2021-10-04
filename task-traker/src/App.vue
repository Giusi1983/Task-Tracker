<template>
<div class="container">
  <Header title="Task Tracker" />
  <Tasks @toggle-reminder="toggleReminder" 
  @delete-task="deleteTask" :tasks="tasks" />
</div>
 </template>

<script>
 import Header from './components/Header.vue';
 import Tasks from './components/Tasks.vue';
 
export default {
  name: "App",
  components: {
    Header,
    Tasks
    
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    deleteTask(id) {
      if(confirm('Are you sure?')) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
     console.log(id)
    }
  },
  created() {
    this.tasks = [
     {
       id:1, 
       text: 'Swimming lesson',
       day:'October 4th at 3:00 p.m',
       reminder: true,
     },
     {
       id:2, 
       text: 'Doctor appointment',
       day:'October 14th at 1:00 p.m',
       reminder: true,
     },
     {
       id:3, 
       text: 'Meeting at office',
       day:'October 6th at 9:00 a.m',
       reminder: true,
     },
    ]
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  border: 1px solid blue; 
  width: 100vh; 
  height:100vh; 
}
</style>
