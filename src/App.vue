<template>
  <div id="app">
    <h1>To-do-list</h1>
    <ToDoForm @todo-added="addToDo"/>
    <ul>
      <li v-for="item in Todoitems" :key="item.id">
        <Todoitem :label="item.label" :done="item.done" :id="item.id" />
      </li>
    </ul>

  </div>
</template>

<script>
import Todoitem from './components/ToDo.vue';
import uniqueId from 'lodash.uniqueid';
import ToDoForm from './components/TodoForm';

export default {
  name: 'app',
  components: {
    Todoitem,
    ToDoForm
  }, 
  data(){
    return{
      Todoitems: [
      { id: uniqueId('todo-'), label: 'Learn Vue', done: false },
      { id: uniqueId('todo-'), label: 'Create a Vue project with the CLI', done: true },
      { id: uniqueId('todo-'), label: 'Have fun', done: true },
      { id: uniqueId('todo-'), label: 'Create a to-do list', done: false }
    ]
    }
  }, 
  methods: {
    addToDo(toDoLabel) {
      console.log('To-do added', toDoLabel);
      this.Todoitems.push({id:uniqueId('todo-'), label: toDoLabel, done:false})
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
</style>
