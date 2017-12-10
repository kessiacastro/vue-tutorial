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
        <novo-todo></novo-todo>
      </div>
    </div>
    <footer class="card-footer">
    </footer>
  </div>
</template>

<script>
import NovoTodo from './NovoTodo'

export default {
  name: 'todo-card',
  components: {
    NovoTodo
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
