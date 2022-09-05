<script setup>
import TodoForm from "./TodoForm.vue";
import TodoList from "./TodoList.vue";
</script>

<template>
    <div class="todo-container">
        <h1 class="todo-title">To do List</h1>
        <todo-form />
        <todo-list />
    </div>
</template>
