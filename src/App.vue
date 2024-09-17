<template>
  <div class="container">
    <fieldset role="group">
      <input type="text" v-model="newTodo">
      <button :disabled="newTodo.length === 0" @click="addTodo">Ajouter</button>
    </fieldset>
    <div v-if="todos.length === 0">
      Vous n'avez pas de tâches à faire :(
    </div>
    <div v-else>
      <ul>
        <li v-for="(todo, index) in sortedTodos" :key="`${todo.date}-${index}`" :class="{completed: todo.completed}">
          <label>
            <input  type="checkbox" :name="todo.title" v-model="todo.completed">
            {{ todo.title }}
          </label>
        </li>
      </ul>
      <label>
        <input type="checkbox" v-model="hideCompleted">
        Masquer les tâches complétées
      </label>
    </div>
  </div>
</template>

<script setup>
import {computed, ref} from "vue";

const todos = ref([{
  "title": "Tache numero 1",
  "completed": true,
  "date": 1
}, {
  "title": "Tache numero 2",
  "completed": false,
  "date": 2
}])
const newTodo = ref('')
const hideCompleted = ref(false)

const addTodo = (e) => {
  todos.value.push({
    title: newTodo.value,
    completed: false,
    date: Date.now()
  })
  newTodo.value = ''
}

const sortedTodos = computed(() => {
  const completedTodos = todos.value.filter(todo => todo.completed)
  const activeTodos = todos.value.filter(todo => !todo.completed)

  completedTodos.sort((a,b) => a.title.localeCompare(b.title))
  activeTodos.sort((a,b) => a.title.localeCompare(b.title))

  const sortedTodos = [...activeTodos, ...completedTodos]

  if (hideCompleted.value === true) {
    return sortedTodos.filter(t => t.completed === false)
  }

  return sortedTodos;
})
</script>

<style scoped>
.completed {
  opacity: .5;
  text-decoration: line-through;
}
</style>
