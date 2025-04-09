<template>
  <nav>
    <button @click="goTo('Hello')">Main</button>
    <button @click="goTo('about')">About</button>
    <button @click="goTo('Skills')">Skills</button>
    <button @click="goTo('Project')">Projects</button>
    <button @click="goTo('Contact')">Contact</button>
  </nav>

</template>

<script setup>
import { defineEmits } from 'vue'
import Hello from './Hello.vue'
import about from './about.vue'

const emit = defineEmits(['change-section'])

function goTo(sectionName) {
  emit('change-section', sectionName)
}
</script>


<style scoped>

  button {
    text-align: center;
    font-size: 1rem;
    color: white;
    font-weight: bold;
    margin: 10px 20px 0 20px;
    width: 10vw;
    height: 5vh;
    background: none;
    border: none;
    transition: font-size 0.3s ease;
  }

  button:hover {
    font-size: 1.2rem;
    cursor: pointer;
  }

</style>