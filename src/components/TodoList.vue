// todoList.vue

<template>
    <div class="w-full">
        <ul v-for="(todo, key) in todoList" :key="todo.id" class="todo-list">
            <li>
                <span :class="{ completed: todo.completed }"
                    >{{ `${key}- ` }}{{ todo.item }}</span
                >
                <button type="button" @click.stop="toggleCompleted(todo.id)">
                    <span>&#10004;</span>
                </button>
                <button type="button" @click="deleteTodo(todo.id)">
                    <span> &#10060; </span>
                </button>
            </li>
        </ul>
        <div class="todo-total">
            <span><b>COMPLETED:</b> {{ completed.length }} </span>
            <span><b>TOTAL:</b>{{ todoList.length }}</span>
        </div>
    </div>
</template>

<script>
import { useTodoListStore } from "@/stores/useTodoListStore";
import { computed } from "vue";
import { storeToRefs } from "pinia";
export default {
    setup() {
        const store = useTodoListStore();
        const { todoList } = storeToRefs(store);
        const { toggleCompleted, deleteTodo } = store;

        // a computed ref
        const completed = computed(() => {
            return store.todoList.filter((todo) => todo.completed === true);
        });

        return { completed, todoList, toggleCompleted, deleteTodo };
    },
};
</script>

<style>
.completed {
    text-decoration: line-through;
}
</style>
