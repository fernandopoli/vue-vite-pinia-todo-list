<script>
import { ref } from "vue";
import { useTodoListStore } from "@/stores/useTodoListStore";
export default {
    setup() {
        const todo = ref("");
        const store = useTodoListStore();

        function addItemAndClear(item) {
            if (item.length === 0) {
                return;
            }
            store.addTodo(item);
            todo.value = "";
        }

        return { todo, addItemAndClear, store };
    },
};
</script>
<template>
    <form @submit.prevent="addItemAndClear(todo)" class="todo-form">
        <input
            class="todo-input"
            placeholder="Add task to the list"
            v-model="todo"
            type="text"
        />
        <button class="todo-btn">Add</button>
    </form>
</template>

<style lang="scss" scoped></style>
