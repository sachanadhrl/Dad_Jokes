<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'

import CardJokes from './components/CardJokes.vue'

let isLoading = ref(false)

const jokes = ref({
  setup: '',
  punchline: ''
})

const generateJokes = async () => {
  isLoading.value = !isLoading.value
  try {
    const res = await axios.get('https://official-joke-api.appspot.com/random_joke')
    isLoading.value = !isLoading.value
    jokes.value = res.data
  } catch (err) {
    throw err
  }
}

onMounted(() => {
  generateJokes()
})

</script>

<template>
  <div class="container p-5">
    <div class="row justify-content-center">
      <CardJokes :jokes="jokes" :loading="isLoading" @generateJokes="generateJokes" />
    </div>
  </div>
</template>
