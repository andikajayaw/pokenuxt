<template>
  <div>
    <div
      class="container mx-auto grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 pt-6 gap-8"
    >
      <div
        class="rounded border-gray-300 dark:border-gray-700 border-dashed border-2 h-24"
        v-for="pokemon in data.results"
      >
        {{ pokemon.name }}
        {{ pokemon.url }}
      </div>
    </div>
  </div>
</template>

<script setup>
import axios from "axios";
const dataPokemon = ref([]);
const { data } = await useFetch("https://pokeapi.co/api/v2/pokemon");
console.log(data.results);
</script>
