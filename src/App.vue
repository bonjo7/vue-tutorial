<template>
  <div id="app">
    <h1>To-Do List</h1>
    <to-do-form @todo-added="addToDo"></to-do-form>
      <ul>
        <li v-for="item in ToDoItems" :key="item.id">
          <to-do-item :label="item.label" v-bind:done="item.done" :id="item.id"></to-do-item>
        </li>
      </ul>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue';
import ToDoForm from './components/ToDoForm';
import uniqueId from 'lodash.uniqueid';

export default {
  name: 'app',
  components: {
    ToDoItem,
    ToDoForm,
  },
  data(){
    return {
      ToDoItems: [
        
      ]
    };
  },
  methods: {
    addToDo(toDoLabel) {
      console.log('To-do added', toDoLabel);
      this.ToDoItems.push({id:uniqueId('todo-'), label: toDoLabel, done: false});
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
