<script setup>
const props = defineProps({
  jokes: Object,
  loading: Boolean
})

const emit = defineEmits(['generateJokes'])
</script>

<template>
  <div class="col-12 col-md-6 bg-white rounded-1 p-4">
    <div v-if="loading" class="d-flex justify-content-center">
      <div class="spinner-border text-primary" role="status">
        <span class="visually-hidden">Loading...</span>
      </div>
    </div>
    <div v-else class="text-end">
      <h4>
        {{ jokes.setup }}
      </h4>
      <p class="fw-bold">
        {{ jokes.punchline }}
        <br>
        😂
      </p>
      <button @click="emit('generateJokes')" class="btn btn-danger">
        Reload ‍💫
      </button>
    </div>
  </div>
</template>