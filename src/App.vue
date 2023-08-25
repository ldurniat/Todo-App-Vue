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

function removeTodo(index) {
    todos.value.splice(index, 1)
}

function markAllDone() {
    todos.value.forEach( (todo) => {
        todo.done = true
    });
}
</script>

<template>
    <h1>Vue 3 Todo  App</h1>
    <form action="" @submit.prevent="addNewTodo">
        <label>New Todo</label>
        <input type="text" v-model="newTodo" name="newTodo">
        <button>Add New Todo</button>
    </form>
    <button @click="markAllDone">Mark All Done</button>
    <button>Remove All Todos</button>

    <ul>
        <li class="todo" v-for="(todo, index)  in todos" :key="todo.id">
            <h3 :class="{done: todo.done}" @click="toggleDone(todo)">{{ todo.content }}</h3>
            <button @click="removeTodo(index)">Remove Todo</button>
        </li>
    </ul>
    
</template>

<style scoped>

.todo {
    cursor: pointer;
}
.done {
    text-decoration: line-through;
}
</style>
