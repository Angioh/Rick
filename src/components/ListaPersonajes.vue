<template>
  <div>
    <p>
      Estamos buscando a <b>{{ entrada }}</b>
    </p>
    <input
      ref="input"
      id="personaje"
      type="text"
      @keydown.enter="filtrarNombre"
      v-model="entrada"
      placeholder="Personaje"
    />
  </div>
  <div
    v-for="personaje in listaPj"
    :key="personaje.id"
    class="place-content-center"
  >
    <Personajes :pj="personaje" />
  </div>
</template>

<script>
import axios from "axios";
import Personajes from "./Personajes.vue";
export default {
  components: {
    Personajes,
  },
  data() {
    return {
      listaPj: [],
      entrada:"",
    };
  },
  mounted() {
    this.listarPersonajes();
  },
  methods: {
    async listarPersonajes() {
      try {
        const response = await axios.get(
          `https://rickandmortyapi.com/api/character/`
        );
        this.listaPj = response.data.results;
        for (let i = 2; i < response.data.info.pages; i++) {
          const response2 = await axios.get(
            `https://rickandmortyapi.com/api/character/?page=${i}`
          );
          response2.data.results.map((x) => this.listaPj.push(x));
        }
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
