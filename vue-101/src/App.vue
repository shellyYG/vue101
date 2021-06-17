<template>
<div class="container"> 
   <Header />
   <AddTask @add-task="addTask" />
   <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
</div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/addTask'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm('Are you sure to delete?')) {
        this.tasks = this.tasks.filter((task)=> task.id !==id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task)=>
        task.id===id? {
          ...task, 
          reminder: !task.reminder
        }: task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Task1',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Task2',
        day: 'March 2nd at 2:30pm',
        reminder: false,
      }
    ]
  }
}
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

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>
