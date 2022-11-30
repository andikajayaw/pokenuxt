<template>
  <div
    class="w-full bg-white rounded-lg shadow-md dark:bg-gray-800 dark:border-gray-700"
  >
    <a href="#">
      <img
        class="p-8 rounded-t-lg hover:scale-125 ease-in duration-300"
        :src="pokemon.sprites.other['official-artwork'].front_default"
        alt="product image"
      />
    </a>
    <div class="px-5 pb-5">
      <a href="#">
        <h5
          class="text-xl font-semibold tracking-tight text-gray-900 dark:text-white uppercase"
        >
          {{ pokemon.name }}
        </h5>
      </a>
      <div class="flex items-center justify-between">
        <span
          class="text-2xl font-bold text-gray-900 dark:text-white uppercase"
          v-for="type in pokemon.types"
          >{{ type.type.name }}</span
        >
        <a
          href="#"
          class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
          >{{ pokemon.id }}</a
        >
      </div>
    </div>
  </div>
</template>

<script setup>
const prop = defineProps(["pokemon"]);
</script>
