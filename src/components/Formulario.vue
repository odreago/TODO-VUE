<script setup>
 const props = defineProps ([ 'cadastraTarefa', 'tarefaTemp', 'trocarFiltro', 'editaTarefaTemp'])
</script>

<template>
    <form @submit.prevent="props.cadastraTarefa">
            <div class="row">
                <div class="col">
                    <input :value="props.tarefaTemp" @input="props.editaTarefaTemp" required type="text" placeholder="digite aqui sua tarefa" class="form-control">
                </div>
                <div class="col-md-1">
                    <button type="submit" class="btn btn-primary">Adicionar</button>
                </div>
                <div class="col-md-2">
                    <select @change="props.trocarFiltro" class="form-control">
                        <option value="todas">todas as Tarefas</option>
                        <option value="pendentes">pendentes</option>
                        <option value="finalizadas">finalizadas</option>
                    </select>
                </div>
            </div>
        </form>
</template>