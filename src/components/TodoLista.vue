<template>
    <div>
        <ul class="list-group">
            <todo-item v-for="todo in todos" :key="todo.id" :todo="todo" />
            <li
                class="List-group-item d-flex justify-content-between align-items-center"
                v-if="todos.length === 0"
            >
                No hay elementos
            </li>
            <todo-footer v-if="todos.length !== 0" />
            <todo-filtros />
        </ul>
    </div>
</template>

<script>
import { computed, inject, provide, ref } from "vue";
import TodoItem from "./TodoItem.vue";
import TodoFooter from "./TodoFooter.vue";
import TodoFiltros from "./TodoFiltros.vue";
export default {
    components: { TodoItem, TodoFooter, TodoFiltros },
    setup() {
        const todosLosItems = inject("todos");

        const estado = ref("todos");

        const todos = computed(() => {
            if (estado.value === "todos") {
                return todosLosItems.value;
            }
            if (estado.value === "activos") {
                return todosLosItems.value.filter(
                    (item) => item.estado === false
                );
            }
            if (estado.value === "completados") {
                return todosLosItems.value.filter(
                    (item) => item.estado === true
                );
            }
        });
        provide("estado", estado);
        return { todos };
    },
};
</script>

<style></style>
