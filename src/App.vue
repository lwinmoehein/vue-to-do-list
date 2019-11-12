<template>

  <div id="app">
    <Header/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteToDo"/>
  </div>
</template>

<script>
import Todos from './components/ToDo'
import Header from './components/layouts/header'
export default {
  name: 'app',
  components: {
    Todos,
    Header
  },
  data(){
    return {
      todos:[
        {
          id:1,
          title:"todo one",
          completed:true,
        },
        {
          id:2,
          title:"todo two",
          completed:false,
        },
        { 
          id:3,
          title:"todo three",
          completed:false,
        },
        {
          id:4,
          title:"todo four",
          completed:true,
        },
      ]
    }
  },
  methods:{
    deleteToDo(id){
      this.todos=this.todos.filter(todo=>todo.id!==id);
    }
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
