<template>
  <div
    class="w-full rounded-lg shadow-md bg-gradient-to-b from-violet-500 to-fuchsia-500 dark:border-gray-700"
  >
    <div
      class="rounded-lg grid grid-cols-2 md:grid-cols-2 lg:grid-cols-2 gap-4"
    >
      <div>
        <div class="p-5 m-5">
          <a href="#">
            <h5
              class="text-2xl font-bold tracking-tight text-gray-900 dark:text-white capitalize"
            >
              {{ pokemon.name }}
            </h5>
          </a>
          <h3
            class="text-lg font-semibold text-gray-900 dark:text-white capitalize"
          >
            Type:
          </h3>
          <div class="flex items-center justify-between">
            <span
              class="text-sm font-semibold text-gray-900 dark:text-white capitalize"
              v-for="type in pokemon.types"
              >{{ type.type.name }}</span
            >
          </div>
          <div class="mt-4 items-end">
            <a
              href="#"
              class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-xl text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
              >{{ pokemon.id }}</a
            >
          </div>
        </div>
      </div>
      <div>
        <div style="background-image: url(~assets/images/pokeball-bg-2.png)">
          <img
            class="w-64 p-8 items-center justify-center rounded-t-lg hover:scale-125 ease-in duration-150"
            :src="pokemon.sprites.other['official-artwork'].front_default"
            alt="product image"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const prop = defineProps(["pokemon"]);

async function bgColor(val) {
  //   :class="bgColor(pokemon.types[0])"

  console.log(val.type.name);
  let bgColor = "bg-gray-800";
  switch (val.type.name) {
    case "grass":
      bgColor = "bg-green-800";
      break;
    case "fire":
      bgColor = "bg-rose-800";
      break;
    case "water":
      bgColor = "bg-blue-800";
      break;
    case "normal":
      bgColor = "bg-gray-800";
      break;
    case "bug":
      bgColor = "bg-lime-800";
      break;
    default:
      break;
  }
  console.log(bgColor);
  return bgColor;
}
</script>
