<template>
  <div id="app">
    <h1 class="ui dividing centered header">Vue.js Todo App</h1>
    <p class="ui dividing centered header">A tutorial from
    <br />
    <a href="https://scotch.io/tutorials/build-a-to-do-app-with-vue-js-2" target="_blank">https://scotch.io/tutorials/build-a-to-do-app-with-vue-js-2</a>
    <br />
    <i>with some small adjustments</i>
    </p>
    <div class='ui three column centered grid'>
      <div class='column'>
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:create-todo="createTodo"></create-todo>
      </div>
    </div>
  </div>
</template>

<script>
import sweetalert from 'sweetalert2'
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo
  },
  data () {
    return {
      todos: [{
        title: 'MOAR Buttons',
        project: 'Buttons!',
        done: false
      }, {
        title: 'Feex that thing.',
        project: 'Someday / Never',
        done: false
      }, {
        title: 'Buttons...',
        project: 'Buttons',
        done: true
      }, {
        title: 'Someding',
        project: 'Dings',
        done: false
      }]
    }
  },
  methods: {
    createTodo (newTodo) {
      this.todos.push(newTodo)
      sweetalert('Success!', 'To-Do created!', 'success')
    }
  }
}
</script>
