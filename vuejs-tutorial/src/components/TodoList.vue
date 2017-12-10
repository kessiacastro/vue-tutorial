<template>
<div class="row">
    <div class="columns">
      <div class="column">
        <div class="field is-grouped" v-for="(tarefa, index) in tarefas">
          <p class="control">
            <a class="button is-rounded is-small check-button" @click="check(index)">
              <span class="icon is-small">
              </span>
            </a>
          </p>
          <p class="control is-expanded" :class="{'checked': tarefa.checked }">{{tarefa.description}}</p>
          <p class="control">
            <a class="button is-danger is-small" @click="remove(index)">
              <span class="icon is-small">
                <i class="fa fa-trash"></i>
              </span>
            </a>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'todo-list',
  props: ['tarefas'],
  data () {
    return {
    }
  },
  methods: {
    check(tarefa) {
      this.$emit('check', tarefa)
    },
    remove(tarefa) {
      this.$emit('remove', tarefa)
    }
  }
}
</script>

<style scoped>
.button {
  border-radius: 50%;
}

.checked {
  text-decoration: line-through;
}

</style>
