<script setup>
    const props = defineProps (['tarefasPendentes'])
</script>

<template>
    <header class="p-5 my-4 bg-light rondend-3">
            <h1>minhas Tarefas</h1>
            <p>Você possui {{props.tarefasPendentes}} Tarefas pendentes</p>
    </header>
</template>