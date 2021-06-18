<template>
<div class="container"> 
   <Header @toggle-add-task="toggleAddTask"
   title="Task Tracker"
   :showAddTask="showAddTask"
   />
   
   <router-view :showAddTask="showAddTask"></router-view>
   <Footer/>
</div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'


export default {
  name: 'App',
  components: {
    Header,
    Footer
  },
  data() {
    return {
      showAddTask: true,
    }
  },
  methods: {
    toggleAddTask() {
        this.showAddTask = !this.showAddTask
      },
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
