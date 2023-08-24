<script setup>
import { ref } from 'vue'

const newTodo = ref('')
const todos   = ref([])

function addNewTodo() {
    todos.value.push({
        id     : Date.now(),
        done   : false,
        content: newTodo.value
    })
    // Clear input 
    newTodo.value = '';
}

function toggleDone(todo) {
    todo.done = !todo.done
}
</script>

<template>
    <h1>Vue 3 Todo  App</h1>
    <form action="" @submit.prevent="addNewTodo">
        <label>New Todo</label>
        <input type="text" v-model="newTodo" name="newTodo">
        <button>Add New Todo</button>
    </form>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
            <h3 @click="toggleDone(todo)">{{ todo.content }}</h3>
        </li>
    </ul>
    
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>
