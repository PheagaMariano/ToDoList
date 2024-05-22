<template>
  <nav class="navbar text-bg-primary">
    <div class="container-fluid">
      <span class="navbar-brand mb-0 h1 text-white">
        {{ titulo }}
      </span>
    </div>
  </nav>
  <div class="mb-3 m-4">
    <label for="exampleFormControlInput1" class="form-label">Nome da tarefa</label>
    <input 
      v-model="nomeTarefa"
      type="text" 
      class="form-control mb-2" 
      id="exampleFormControlInput1" 
      placeholder="escreva uma tarefa">
    <button type="button" class="btn btn-primary" @click="adicionarTarefa(nomeTarefa)">adicionar tarefa</button>
  </div>
  <div class="list-group m-4">
    <a href="#" class="list-group-item list-group-item-action" v-for="lista in listaTarefa">
      {{ lista.tarefa }}
    </a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nomeTarefa: '',
      titulo: 'Lista de tarefas',
      listaTarefa: [
        {
          tarefa: 'fazer uma caminha às 05:00'
        },
        {
          tarefa: 'almoçar ao 12:00'
        },
        {
          tarefa: 'ir pra casa 16:30'
        }
      ]
    }
  },
  methods: {
    adicionarTarefa(nome) {
      this.listaTarefa.unshift({ tarefa: nome });
      this.nomeTarefa = '';
      localStorage.setItem("listaTarefa",JSON.stringify(this.listaTarefa));
    }
  },
  mounted(){
    this.listaTarefa = JSON.parse(localStorage.getItem("listaTarefa"));
  }
}
</script>