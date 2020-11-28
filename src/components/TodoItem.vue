<template>
    <li class="list-group-item d-flex justify-content-between align-items-center">
        <!--Span con rol button, que list los items-->
        <!--Evento click(cambiarEstado) -->
        <span role="button" @click="cambiarEstado(todo.id)" :class="{'tachado': todo.estado}">
            {{ todo.texto }}
        </span>
        <!--Span con rol button y evento click(eliminarItem) -->
        <span role="button" @click="eliminarItem(todo.id)">
            <i class="fas fa-times "></i
        ></span>
    </li>
</template>

<script>
import { inject } from "vue";
export default {
    props: {
        todo: {
            type: Object,
            required: true,
        },
    },
    setup() {
        const todos = inject("todos");
        // Eliminta el item atravez de la id
        const eliminarItem = (id) => {
            todos.value = todos.value.filter((item) => item.id !== id);
        };
        // Cambia el estado de los item a true
        const cambiarEstado = (id) => {
            todos.value = todos.value.map(item => {
                if(item.id === id){
                    item.estado = true;
                }
                return item
            })
        };

        return { eliminarItem, cambiarEstado };
    },
};
</script>

<style>
.tachado {
    text-decoration: line-through;
}
</style>
