<template>
    <div>
        <h1>Todo App</h1>
    </div>
    <todo-form />
    <todo-lista />
</template>

<script>
import { provide, ref, watchEffect } from "vue";
import TodoForm from "./TodoForm.vue";
import TodoLista from "./TodoLista.vue";
export default {
    components: { TodoForm, TodoLista },
    setup() {
        const todos = ref([]);
        provide("todos", todos);

       if (localStorage.getItem("todos")) {
            todos.value = JSON.parse(localStorage.getItem("todos"));
        }

        watchEffect(() => {
            localStorage.setItem("todos", JSON.stringify(todos.value));
        });
    },
};
</script>

<style></style>
