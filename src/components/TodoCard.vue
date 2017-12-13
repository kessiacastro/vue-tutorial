<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title has-text-left">
       {{ today }}
      </p>
      <div class="has-text-right">
        <p class="card-header-title">{{tarefas.length}} tarefas</p>
      </div>
    </header>
    <div class="card-content">
      <div class="content">
        <novo-todo @novaTarefa="adicionarTarefa"></novo-todo>
      </div>
      <div class="content">
        <todo-list :tarefas="tarefas" @check="checkTarefa" @remove="removerTarefa"></todo-list>
      </div>
    </div>
  </div>
</template>

<script>
import NovoTodo from './NovoTodo'
import TodoList from './TodoList'

export default {
  name: 'todo-card',
  components: {
    NovoTodo,
    TodoList
  },
  data () {
    return {
      dias: ['Domingo', 'Segunda', 'Terça', 'Quarta', 'Quinta', 'Sexta', 'Sábado'],
      meses: ['Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio', 'Junho', 'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'],
      tarefas: []
    }
  },
  computed: {
    today: function() {
      let date = new Date()
      return `${this.dias[date.getDay()]}, ${date.getDate()} de ${this.meses[date.getMonth()]}`
    }
  },
  methods: {
    adicionarTarefa(tarefa) {
      let nova_tarefa = {'description': tarefa, 'checked': false}
      this.tarefas.push(nova_tarefa)
    },
    checkTarefa(tarefa) {
      this.tarefas[tarefa]['checked'] = !this.tarefas[tarefa]['checked']
    },
    removerTarefa(tarefa) {
      this.$delete(this.tarefas, tarefa)
    }
  }
}
</script>

<style>
.card {
  border-radius: 10px;
}

.card-header-title {
  color: #636368;
}
</style>
