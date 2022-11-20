<template>
  <div
    class="bg-green-600 box-content h-65 w-38 border-2 border-green-700 p-4 m-2 rounded-lg sm-text-center font-Roboto"
  >
    <img :src="pj.image" />
    <p>{{ pj.name }}</p>
    <p>'{{ pj.species }}'</p>
    <p>{{ pj.status }}</p>
  </div>
</template>

<script>
export default {
  props: {
    pj: {
      type: Object,
    },
  },
};
</script>

<style lang="scss" scoped></style>
