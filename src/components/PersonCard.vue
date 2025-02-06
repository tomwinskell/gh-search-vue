<script setup lang="ts">
const props = defineProps<{
  name: string;
  image: string;
}>();
</script>

<template>
  <div class="col">
  <div class="card">
    <img :src="props.image" class="card-img-top" alt="..." />
    <div class="card-body">
      <h5 class="card-title">{{ props.name }}</h5>
    </div>
  </div>
  </div>
</template>

<style scoped></style>
