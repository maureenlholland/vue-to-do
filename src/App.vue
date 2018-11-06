<template>
  <div id="app">
    <AppHeader />
    <ToDoList 
      :todos="todos" 
      @toDoDeleted="deleteFromList" 
      @toDoUpdated="updateList"/>
    <AddToDo 
      @addNew="addToList"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import AddToDo from './components/AddToDo.vue';
import ToDoList from './components/ToDoList.vue';

export default {
  name: 'app',
  data: () => {
    return  {
      todos: [],
    }
  },
  components: {
    AppHeader: Header,
    AddToDo,
    ToDoList
  },
  methods: {
    addToList(todo){
      this.todos.push({
        todo,
        update: false
      });
    },
    deleteFromList(i){
       this.todos.splice(i, 1);
    },
    updateList(i, newTodo){
      this.todos.splice(i, 1, newTodo);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.list {
  width: 100%;
  max-width: 200px;
  margin: 0 auto;
  text-align: left;
}
</style>
