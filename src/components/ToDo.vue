<template>
    <div>
        <div v-for="todo in todos" v-bind:key="todo.key">
            <ToDoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
        </div>
    </div>
</template>
<script>
import ToDoItem from "./ToDoItem.vue"
export default {
    name:"Todos",
    props:["todos"],
    components:{
        ToDoItem
    },
}
</script>
<style scoped>

</style>