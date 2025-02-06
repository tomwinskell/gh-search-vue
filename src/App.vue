<script setup lang="ts">
import PersonCard from './components/PersonCard.vue';
import { ref } from 'vue';
import type { Ref } from 'vue';
import SearchForm from './components/SearchForm.vue';

const people: Ref<{ name: string | null; image: string | null }[]> = ref([]);

async function handleSearch(query: string) {
  const res = await fetch(
    'https://api.github.com/repos/facebook/react/commits/' + query
  );
  const data = await res.json();
  people.value.push({
    name: data.author.login || null,
    image: data.author.avatar_url || null,
  });
}
</script>

<template>
  <div class="container mt-5">
    <div class="container text-center mb-3">
      <div class="row row-cols-2 row-cols-md-3 g-3">
        <PersonCard
          v-for="(person, index) in people"
          :key="index"
          :name="person.name || 'Unknown'"
          :image="person.image || 'defaultImage.png'"
        />
      </div>
    </div>

    <SearchForm @search="handleSearch" />
  </div>
</template>

<style scoped></style>
