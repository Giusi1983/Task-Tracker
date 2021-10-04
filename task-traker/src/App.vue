<template>
<div class="container">
  <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask"/>
  <div v-show="showAddTask">
  <AddTask @add-task="addTask" />
  </div>
  <Tasks @toggle-reminder="toggleReminder" 
  @delete-task="deleteTask" :tasks="tasks" />
</div>
 </template>

<script>
 import Header from './components/Header.vue';
 import Tasks from './components/Tasks.vue';
 import AddTask from './components/AddTask.vue'; 
 
export default {
  name: "App",
  components: {
    Header,
    Tasks, 
    AddTask
    
  },
  data() {
    return {
      tasks: [], 
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },

    addTask(task) {
      this.tasks = [...this.tasks, task]
    },

    deleteTask(id) {
      if(confirm('Are you sure?')) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => 
      task.id === id ? {...task, reminder: !task.reminder } : task
      )
    },
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
  display: flex;
  justify-content: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  border: 1px solid blue; 
  width: 100vh; 
  height:100%; 
}

h1 {
  margin-left:5px; 
}

@media only screen and (max-width: 600px) {
  h1 {
    font-size:24px;
  }

}  
</style>
