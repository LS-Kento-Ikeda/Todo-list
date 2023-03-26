<script>
import { ref } from 'vue'

export default {
  name:'HelloWorld',
  data: () => ({
    todos: [],
    todo: {
      name:"",
      description:"",
      deadline:"",
      checked:"false"
    },
    name:"todos",
    stuatas:""
  }),
  methods: {
    read() {
      const data = localStorage.getItem(this.name)
      this.todos = JSON.parse(data)
    },

    create() {
      this.todos.push(this.todo)
      localStorage.setItem(this.name,JSON.stringify(this.todos))
      this.todo= {
      name:"",
      description:"",
      deadline:"",
      completed:""
      }
    },

    deleteTodo(todo) {
      this.todos = this.todos.filter((item) => item.name !== todo.name)
      localStorage.setItem(this.name,JSON.stringify(this.todos))
    },

    statusChage(){
      if(checked){
        
      }
    }
  }
}

const count = ref(0)
</script>

<template>
  <div class="HelloWorld">
    <h1>Todo</h1>
    <h3>Enter todo</h3>
    <p>Todo</p>
    <input v-model="todo.name">
    <p>Description</p>
    <input v-model="todo.description">
    <p>Deadline</p>
    <input v-model="todo.deadline">
    <br>
    <button style="submit" @click="create">Create</button>
    <button style="submit" @click="read">Read</button>
    <hr>
      <div v-for="todo in todos" :key="todo.name">
        <button style="submit" @click="deleteTodo(todo)">Delete</button>
        <button style="submit" @click="statusChage">Change</button>
        <input type="checkbox" id="checkbox" @input="statusChage">
        <div :class="status">
          <li>Name: {{ todo.name }}</li>
          <li>Description: {{ todo.description }}</li>
          <li>Deadline: {{ todo.deadline }}</li>
        </div>
        <hr>
      </div>
  </div>
</template>

<style scoped>

</style>
