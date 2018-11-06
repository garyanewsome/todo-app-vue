<template>
  <div>
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="(todo, index) in todos" :todo.sync="todo" :key="index"></todo>
  </div>
</template>

<script type = "text/javascript" >
import sweetalert from 'sweetalert2'
import Todo from './Todo'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      sweetalert({
        title: 'Are you sure?',
        text: 'This Todo will be permanently deleted!',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#007800',
        cancelButtonColor: '#780000',
        cancelButtonText: 'NOOOOOOOOO!',
        confirmButtonText: 'Do it, delete it, do it NOW!'
      })
        .then((result) => {
          if (result.value) {
            const todoIndex = this.todos.indexOf(todo)
            this.todos.splice(todoIndex, 1)
            sweetalert('Deleted!', 'Your To-Do has been deleted.', 'success')
          } else {
            sweetalert('SAVED', 'Your item remains intact! That was scary.', 'info')
          }
        })
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
      sweetalert('Success!', 'To-Do completed!', 'success')
    }
  }
}
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>
