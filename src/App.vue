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
}
</script>

<template>
    <h1>Vue 3 Todo  App</h1>
    <form action="" @submit.prevent="addNewTodo">
        <label>New Todo</label>
        <input type="text" v-model="newTodo" name="newTodo">
        <button>Add New Todo</button>
    </form>

    <div v-for="todo in todos">
        <h3>{{ todo.content }}</h3>
    </div>
</template>

<style scoped>

</style>
