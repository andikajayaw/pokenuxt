<template>
  <div>
    <article class="overflow-hidden rounded-lg shadow-lg">
      <a href="#">
        <img
          class="block h-auto"
          :src="pokemon.sprites.other['official-artwork'].front_default"
        />
      </a>

      <header
        class="flex items-center justify-between leading-tight p-2 md:p-4"
      >
        <h1 class="text-lg">
          <a class="no-underline hover:underline text-black" href="#">
            {{ pokemon.name }}
          </a>
        </h1>
        <h1 class="text-lg">
          {{ pokemon.id }}
        </h1>
        <ul>
          <li v-for="type in pokemon.types">{{ type.type.name }}</li>
        </ul>
      </header>
    </article>
  </div>
</template>

<script setup>
const prop = defineProps(["pokemon"]);
</script>
