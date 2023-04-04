<script setup lang="ts">
import {ref, onMounted, computed,watch} from 'vue'

const todos = ref([])
const name = ref('')
const input_content = ref('')
const input_category = ref(null)
watch(name, (newVal) => {
  localStorage.setItem('name', newVal)
})
onMounted(() => {name.value = localStorage.getItem('name') || ''})
const addTodo = () => {}
</script>

<template>
<main class="app">
  <section class="greeting">
    <h1 class="title">Heyho

      <input type="text" placeholder="name here" v-model="name"/>
    </h1>
  </section>
  <section class="create todos">
    <h3>Add a todo</h3>
    <form @submit.prevent="addTodo">
      <h4>What do you need to do?</h4>
      <input
        type="text"
        placeholder="e.g. create youtube video"
        v-model="input_content"
      />
      <h4>Pick a category</h4>
      <label>
        <input 
          type="radio" 
          name="category" 
          id="category1"
          value="business"
          v-model="input_category"/>
          <span class="bubble business"></span>
          <div>Business</div>
      </label>
      <label>
        <input 
          type="radio" 
          name="category" 
          id="category1"
          value="personal"
          v-model="input_category"/>
          <span class="bubble personal"></span>
          <div>Personal</div>
      </label>
      
    </form>
  </section>
</main>
</template>

<style scoped>

</style>
