<template>
  <div class="container">
    <h1 class="text-center">Simple Todo</h1>
    <form @submit.prevent="addTodo">
      <div class="form-group">
        <label for="newTodo"></label>
        <input v-model="newTodo" type="text" class="form-control" id="exampleInputEmail1" aria-describedby="new Todo" placeholder="Enter a new todo">
        <!-- <small id="newTodoHelp" class="form-text text-muted">Please enter a new todo...</small> -->
      </div>
      <button type="submit" class="btn btn-primary">Add Todo</button>
    </form>
    <div class="mt-5">
      <ul class="list-group">
        <li v-for="(todo, i) in todos" :key="i" class="list-group-item">
          <span :class="{
            isDone: todo.done
          }">
          {{todo.title}}</span>
          <button 
            @click="markDone(todo)" 
            v-show="!todo.done" 
            class="btn btn-success float-right font-weight-bold">Done</button>
            <button
            @click="deleteTodo(i)" 
            v-show="todo.done" 
            class="btn btn-danger float-right mr-2 font-weight-bold">Delete</button>
        </li>
      </ul>
    </div>

  </div>
</template>

<script>
export default {
  name: 'SimpleTodo',
  props: {},
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  mounted(){
    if (localStorage.todos) {
      this.todos = JSON.parse(localStorage.todos)
    }
  },
  watch: {
    todos: {
      handler(){
        localStorage.todos = JSON.stringify(this.todos)
      },
      deep: true
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        title: this.newTodo,
        done: false
      })
      this.newTodo = ''
      
    },
    markDone(todo){
      todo.done = true
    },
    deleteTodo(index){
      this.todos.splice(index, 1)
      
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.isDone {
  text-decoration: line-through
}
</style>
