<template>
  <div id="app">
    <div class="container">
      <Modal  v-on:add-habit="addHabit"/>
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
  </div>
</template>

<script>

import Todos from '../components/Todos';
import Modal from '../components/Modal';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Modal,
    Todos
  },
  data(){
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todos = this.todo.filter(todo => todo.id !== res.data.id))
        .catch(err => console.log(err));
    },

    addHabit(newHabit) {
      const { title, completed } = newHabit;
      axios.post('https://jsonplaceholder.typicode.com/todos', { title, completed })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
    }
  },

  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=6')
      .then(res =>this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style lang="scss">
   @import '../assets/scss/modules/home.scss';
</style>
