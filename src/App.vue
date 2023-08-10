<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { useMessageStore } from './stores/message';
import { storeToRefs } from 'pinia';

const store = useMessageStore()
const { message } = storeToRefs(store)

</script>

<template>
  <header class="max-h-screen leading-normal flex flex-col justify-center bg-pink-300 margin-bottom: 50px">
    <div id="flashMessage" v-if="message" class="bg-yellow-100 transition duration-3000">
      <h4 class="text-20"> {{ message }}</h4>
    </div>
    <nav class="p-10 font-bold">
      <RouterLink class="mx-2 text-xl text-blue-800 hover:text-red-500" :to="{ name: 'event-list' }">Home</RouterLink>
      <RouterLink class="mx-2 text-xl text-blue-800 hover:text-red-500" :to="{ name: 'about' }">About</RouterLink>
      <RouterLink class="mx-2 text-xl text-blue-800 hover:text-red-500" :to="{ name: 'organizer' }">Organizer</RouterLink>
      <RouterLink class="mx-2 text-xl text-blue-800 hover:text-red-500" :to="{ name: 'student' }">Student</RouterLink>
    </nav>
  </header>
  <RouterView />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

h4 {
  font-size: 20px;
}

</style>