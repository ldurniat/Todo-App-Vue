<script setup>
import { ref } from 'vue'

const newTodo = ref('')
const todos   = ref([])

function addNewTodo() {
    console.log("Send form")
}
</script>

<template>
    <h1>Vue 3 Todo  App</h1>
    <form action="" @submit.prevent="addNewTodo">
        <label>New Todo</label>
        <input type="text" v-model="newTodo" name="newTodo">
        <button>Add New Todo</button>
    </form>
</template>

<style scoped>

</style>
