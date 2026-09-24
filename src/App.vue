<script setup>
import { reactive } from 'vue';


    const estado = reactive({
        filtro: 'todas',
        tarefaTemp: '',
        tarefas: [
            {
                titulo: 'Estudar ES6',
                finalizada: false,
            },
            {
                titulo: 'estudar SAAS',
                finalizada:false,
            },
            {
                titulo: 'Ir para a academia',
                finalizada:true,
            }            
        ]
    })

    const getTarefasPendentes = () => {
      return estado.tarefas.filter(tarefa => tarefa.finalizada === false)
    }

    const getTarefasFinalizadas = () => {
        return estado.tarefas.filter(tarefa => tarefa.finalizada)
    }

    const getTarefasFiltradas = () => {
        const { filtro } = estado;

        switch (filtro) {
            case 'pendentes':
                return getTarefasPendentes();
            case 'finalizadas':
                return getTarefasFinalizadas();
            default:
                return estado.tarefas;
        }
    }

    const cadastraTarefa = () => {
        const tarefaNova = {
            titulo: estado.tarefaTemp,
            finalizada: false,
        }
        estado.tarefas.push(tarefaNova);
        estado.tarefaTemp = '';
    }

</script>

<template>

    <div class="container">
        <header class="p-5 my-4 bg-light rondend-3">
            <h1>minhas Tarefas</h1>
            <p>Você possui {{getTarefasPendentes().length}} Tarefas pendentes</p>
        </header>
        <form @submit.prevent="cadastraTarefa">
            <div class="row">
                <div class="col">
                    <input :value="estado.tarefaTemp" @change="e => estado.tarefaTemp = e.target.value" required type="text" placeholder="digite aqui sua tarefa" class="form-control">
                </div>
                <div class="col-md-1">
                    <button type="submit" class="btn btn-primary">Adicionar</button>
                </div>
                <div class="col-md-2">
                    <select @change="e => estado.filtro = e.target.value" class="form-control">
                        <option value="todas">todas as Tarefas</option>
                        <option value="pendentes">pendentes</option>
                        <option value="finalizadas">finalizadas</option>
                    </select>
                </div>
            </div>
        </form>
        <ul class="list-group mt-4">
            <li class="list-group-item" v-for="tarefa in getTarefasFiltradas()">
                <input @change="e => tarefa.finalizada = e.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
                <label :class="{done: tarefa.finalizada}" class="ms-3" :for="tarefa.titulo">
                    {{ tarefa.titulo }}
                </label>    
            </li>
        </ul>
    </div>

</template>

<style scoped>

.done{
    text-decoration: line-through;
}

</style>
