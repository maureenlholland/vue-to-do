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
html {
  box-sizing: border-box;
  --main: #42b983;
  --second: #476582; 
}
*, *:before, *:after {
  box-sizing: inherit;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  margin-bottom: 0;
}
input {
  padding: 5px;
  outline: 1px solid var(--main);
}
.todo__list {
  padding: 20px;
}
.todo__list p{
  margin: 0;
}
.list {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  text-align: left;
}
.list li {
  width: 100%;
  margin: 10px 0;
  padding: 10px;
  border: 1px solid var(--second);
}
.list div {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.list button {
  display: inline-block;
  margin-left: auto;
}
button,
input[type="submit" i] {
  border-radius: 0 !important;
  padding: 5px 10px;
  text-transform: uppercase;
  color: white;
  border: 2px solid transparent;
  font-weight: bold;
  transition: background 0.3s, color 0.3s, border 0.3s;
  outline: none;
}
.action {
  background: var(--main);
}
.action:hover,
.action:focus {
  background: white;
  border: 2px solid var(--main);
  color: var(--main);
}
.warning {
  background: var(--second);
}
.warning:hover,
.warning:focus {
  background: white;
  border: 2px solid var(--second);
  color: var(--second);
}
</style>
