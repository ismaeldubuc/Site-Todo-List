<script setup>
import { ref, onMounted, computed, watch } from 'vue'

const todos = ref([])
const name = ref('')

const input_content = ref('')
const input_category = ref(null)

const todos_asc = computed(() => todos.value.sort.sort((a, b) => {
  return b.createdAt = a.createdAt
}))

const addTodo = () => {}
watch(name, (newVal) => (
    localStorage.setItem('name', newVal)
))

onMounted(() => {
  name.value = localStorage.getItem('name') || ''
})
</script>

<template>

  <main class="app">

    <section class="greeting">
      <h2 class="title">
        Quoi de neuf, <input type="text" placeholder="Name here" v-model="name" />
      </h2>
    </section>

    <section class="create-todo">
      <h3>CREER UNE TACHE</h3>

      <form @submit.prevent="addTodo">
        <h4>De quoi est composé votre liste des tâches ?</h4>
        <input 
          type="text" 
          placeholder="faire une vidéo" 
          v-model="input_content" />

        <h4>Choissisez une catégorie</h4>
      </form>
    </section>
  </main>

</template>
