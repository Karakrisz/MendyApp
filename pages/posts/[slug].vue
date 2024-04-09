<script setup>
import { ref } from 'vue'

const route = useRoute()
const itemPost = ref(null)
const error = ref(null)
const loading = ref(false)

const fetchData = async () => {
  loading.value = true
  try {
    const response = await fetch(
      `http://127.0.0.1:8000/json-posts/${route.params.slug}`
    )
    if (!response.ok) throw new Error('Hiba történt a lekérés során')
    const data = await response.json()
    itemPost.value = data.length > 0 ? data[0] : null
  } catch (e) {
    error.value = e.message
  } finally {
    loading.value = false
  }
}

fetchData()
</script>

<template>
  <div v-if="loading">Betöltés folyamatban...</div>
  <div v-else-if="error">Hiba történt: {{ error }}</div>
  <div v-else-if="itemPost">
    <img
      :src="`http://127.0.0.1:8000/storage/${itemPost.image}`"
      alt="{{ itemPost.title }}"
    />
    <h2>{{ itemPost.title }}</h2>
    <p v-html="itemPost.body"></p>
  </div>
  <div v-else>Nincs megjeleníthető adat.</div>
</template>
