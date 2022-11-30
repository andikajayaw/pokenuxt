<template>
  <div>
    <div class="container my-12 mx-auto px-4 md:px-12">
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
        <div
          class="my-1 px-1 w-full md:w-1/2 lg:my-4 lg:px-4 lg:w-1/3"
          v-for="pokemon in dataSorted"
        >
          <Card :pokemon="pokemon" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import axios from "axios";

const dataPokemon = ref([]);

const dataSorted = computed(() =>
  dataPokemon.value.sort((a, b) => {
    return a.id > b.id ? 1 : -1;
  })
);

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
    })
    .catch(function (error) {
      console.log(error);
    });
}
(async () => {
  await getDataPokemon();
})();
</script>
