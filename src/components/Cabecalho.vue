<script setup>
    const props = defineProps (['tarefasPendentes'])
</script>

<template>
    <header class="p-5 my-4 bg-light rondend-3">
            <h1>minhas Tarefas</h1>
            <p v-if="props.tarefasPendentes > 0">Você possui {{props.tarefasPendentes}} Tarefas pendentes</p>
            <p v-else> Você não tem tarefas pendentes</p>
    </header>
</template>