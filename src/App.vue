<template>
  <div class="place-content-center">
    <ListaPersonajes />
    <p>Hola mundo</p>
  </div>
</template>

<script>
import ListaPersonajes from "./components/ListaPersonajes.vue";
export default {
  components: { ListaPersonajes},
  data() {
    return {
      busqueda: "",
    };
  },
  methods: {
    recibir(newbusqueda) {
      this.busqueda = newbusqueda;
    },
  },
};
</script>

<style lang="scss" scoped></style>
