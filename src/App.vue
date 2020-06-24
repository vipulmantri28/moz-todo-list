<template>
  <div id="app">
    <h1>To-Do List {{recentItem}}</h1>
    <to-do-form @todo-added = "addToDo()"></to-do-form>
    <ul>
      <li v-for="item in ToDoItems" :key="item.id">
        <to-do-item :label="item.label" :done="item.done" :id="item.id"></to-do-item>
      </li>
    </ul>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue';
import uniqueId from 'lodash.uniqueid' ;
import ToDoForm from './components/ToDoForm';

export default{
  name: 'app',
  components:{
    ToDoItem,
    ToDoForm
  },
  data() {
    return {
      ToDoItems: [
        {id: uniqueId('todo-'), label: 'learn Vue', done:false},
        {id: uniqueId('todo-'), label: 'Create a Vue project using CLI', done:true},
        {id: uniqueId('todo-'), label: 'Have Fun', done:true},
        {id: uniqueId('todo-'), label: 'Create a to-do list', done:false}
      ],
      recentItem: ''
    };
  },
  methods: {
    addToDo(toDoLabel) {
      this.recentItem = toDoLabel
      this.ToDoItems.push({id: uniqueId('todo-'), label: toDoLabel, done:false});
    }
  }
};
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
