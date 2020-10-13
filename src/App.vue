<template>
  <div id="app">
    <h1>To Do List</h1>
      <ul>
        <li v-for="(task, index) in tasks" v-bind:class="task.priority? 'low':'high' " :key="index">
          <span class="task">{{task.name}}  </span>
          <span class="complete" v-if="task.priority">Low Priority</span>
          <button class="tickOff" v-if="!task.priority" v-on:click="markPriority(index)">High Priority</button>
        </li>
      </ul>

      <form v-on:submit.prevent='addTask'>
        <label for="new-task">Add New Task:</label>
        <input type="text" id='new-task' v-model="newTask">
        <input type="submit" value="Add Task">

      </form>

  </div>
</template>

<script>
export default {
data(){
  return {
    tasks:[
      {name: "Walk Cat", priority: false},
      {name: "Wash Chocolate Teapot", priority: false},
      {name: "Buy Tartan Paint", priority: true}
    ],
    newTask: "",
  }
},

methods: {
  addTask: function(){
    this.tasks.push({
      name: this.newTask,
      priority: false,
    })
    this.newTask = ""
  },
  markPriority: function(index){
    this.tasks[index].priority = true
  }
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

.complete {
  background: chartreuse;
  margin: 5px;
  border: green solid 2px;
  padding: 5px;
  text-align: right;
  align-content: right;
}

ul > li {
  text-align: left;
  padding: 20px;
  list-style-type: none;
  border: black solid 2px;
  justify-content: space-between;
}

ul {
  text-decoration: none;
}

.tickOff {
  background: lightpink;
  border: red solid 2px;
  text-align: right;

}
</style>
