<template>
  <div>
    <div class="container my-12 mx-auto px-4 md:px-12">
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
        <!-- Column -->
        <div
          class="my-1 px-1 w-full md:w-1/2 lg:my-4 lg:px-4 lg:w-1/3"
          v-for="pokemon in dataPokemon"
        >
          <!-- Article -->
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
          <!-- END Article -->
        </div>
        <!-- END Column -->
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import axios from "axios";
const dataPokemon = ref([]);
const { data } = await useFetch("https://pokeapi.co/api/v2/pokemon");
async function getDataPokemon() {
  await axios
    .get("https://pokeapi.co/api/v2/pokemon")
    .then(function (response) {
      // handle success
      let res = response.data.results;
      res.filter(async (x) => {
        const [resPokemon] = await Promise.all([
          await axios
            .get(x.url)
            .then(function (response) {
              // handle success
              console.log(response.data.id);
              return response.data;
            })
            .catch(function (error) {
              console.log(error);
            }),
        ]);
        dataPokemon.value.push(resPokemon);
      });
      dataPokemon.value.sort((a, b) => {
        return a.id > b.id ? 1 : -1;
      });
    })
    .catch(function (error) {
      console.log(error);
    });
  //   console.log(dataPokemon.value);
}
(async () => {
  await getDataPokemon();
})();
</script>
