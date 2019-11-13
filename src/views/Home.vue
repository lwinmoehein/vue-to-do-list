<template>

  <div id="app">
    <AddToDo v-on:add-todo="addToDo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteToDo"/>
  </div>
</template>

<script>
import axios from 'axios'
import AddToDo from '../components/AddToDo'
import Todos from '../components/ToDo'

export default {
  name: 'home',
  components: {
    Todos,
    AddToDo
  },
  data(){
    return {
      todos:[
       
      ]
    }
  },
  methods:{
    deleteToDo(id){
      this.todos=this.todos.filter(todo=>todo.id!==id);
    },
    addToDo(newToDo){
      this.todos=[...this.todos,newToDo];
    }
  }
  ,
   created(){
        axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(res=>this.todos=res.data);
    }

}
</script>

<style>
 * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>
