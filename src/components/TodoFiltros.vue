<template>
    <div class="card mt-3">
        <div
            class="card-body d-flex justify-content-between align-items-center"
        >
            <span role="button" @click="fitrarItem('activos')">Activos</span>
            <span rule="button" @click="fitrarItem('todos')"> Todos</span>
            <span rule="button" @click="fitrarItem('completados')"
                >Completos</span
            >
        </div>
    </div>
</template>

<script>
import { inject } from "vue";
export default {
    setup() {
        const estado = inject("estado");
        const fitrarItem = (valor) => {
            estado.value = valor;
        };

        return { fitrarItem };
    },
};
</script>

<style></style>
