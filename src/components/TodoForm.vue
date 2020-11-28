<template>
    <form @submit.prevent="agregarTarea">
        <input
            type="text"
            class="from-control my-3"
            placeholder="Ingrese Tarea"
            v-model.trim="texto"
        />
    </form>
</template>

<script>
import { inject, ref } from "vue";
export default {
    name: "TodoForm",
    setup() {
        const todos = inject("todos");
        const texto = ref("");
        const agregarTarea = () => {
            if (texto.value === "") {
                console.log("Texto esta vacio");
                return;
            }
            const todo = {
                id: Date.now(),
                texto: texto.value,
                estado: false,
            };
            todos.value.push(todo);
            texto.value = "";
        };
        return { agregarTarea, texto };
    },
};
</script>

<style></style>
