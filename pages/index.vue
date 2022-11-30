<template>
  <div>
    <div
      class="container mx-auto grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 pt-6 gap-8"
    >
      <div
        class="rounded border-gray-300 dark:border-gray-700 border-dashed border-2 h-24"
        v-for="pokemon in resPokemon"
      >
        <HelloWorld />
        <pre>{{ pokemon }}</pre>
      </div>
    </div>
  </div>
</template>

<script setup>
import axios from "axios";

const resPokemon = async () => {
  return await axios
    .get(`https://pokeapi.co/api/v2/pokemon`)
    .then((response) => response.results)
    .catch((error) => alert(error.message));
};
console.log(resPokemon());
</script>
