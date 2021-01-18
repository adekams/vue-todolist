<template>
  <div id="app">

    
    <todo-list :todos="todos" 
      v-on:delete-todo="deleteTodo">
    </todo-list>
    
    <add-todo @add-todo="addTodo"></add-todo>
  </div>
</template>

<script>
import TodoList from "./components/Todolist";
import AddTodo from './components/AddTodo';

export default {
  name: 'App',
  components: {
    TodoList,
    AddTodo
  },
  data() {
    return {
      todos: [
        // {
        //   id: 1,
        //   title: 'Workout',
        //   completed: false
        // },
        // {
        //   id: 2,
        //   title: 'Cook',
        //   completed: false
        // },
        // {
        //   id: 3,
        //   title: 'Clean',
        //   completed: false
        // },
        // {
        //   id: 4,
        //   title: 'Work',
        //   completed: false
        // },
      ],
    }
  },

  methods: {
    addTodo(newTodo) {     
      this.todos = [...this.todos, newTodo];   
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId) 
    }
  },
  
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
  max-width: 1100px;
  margin: auto;
}
</style>
