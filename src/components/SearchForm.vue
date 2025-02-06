<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits<{
  (event: 'search', query: string): void;
}>();

const query = ref('');

const triggerSearch = () => {
  emit('search', query.value);
  query.value = '';
};
</script>

<template>
  <div class="input-group input-group-lg mb-3">
    <span class="input-group-text" id="inputGroup-sizing-lg">Search</span>
    <input
      type="text"
      class="form-control"
      aria-label="Search input"
      aria-describedby="inputGroup-sizing-lg"
      v-model="query"
    />
  </div>
  <button @click="triggerSearch" class="btn btn-primary btn-lg">Submit</button>
</template>

<style scoped></style>
