<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <Footer />
  </div>
</template>

<script>
  import Header from './components/layout/Header';
  import Todos from './components/Todos';
  import AddTodo from './components/AddTodo';
  import Footer from './components/layout/Footer';
  import axios from 'axios';

  export default {
    name: 'app',
    components: {
      Header,
      Todos,
      AddTodo,
      Footer
    },
    data() {
      return {
        todos: []
      }
    },
    methods: {
      deleteTodo(id) {
        axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
          .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
          .catch(err => console.log(err));
      },
      addTodo(newTodo) {
        const { title, completed } = newTodo;
        axios.post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
          .then(res => this.todos = [...this.todos, res.data])
          .catch(err => console.log(err));
      }
    },
    created() {
      axios.get('https://jsonplaceholder.typicode.com/todos')
        .then(res => this.todos = res.data)
        .catch(err => console.log(err));
    }
  }
</script>

<style>
  body {
    margin: 0;
  }
  #app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  .btn:hover {
    background: #666;
  }
</style>
