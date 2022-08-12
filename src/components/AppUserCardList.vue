<template>
  <div>
    <div
      class="p-2"
      style="width: 18rem; margin: 0 auto"
      v-for="el in list"
      :key="el.email"
    >
      <img :src="el.picture.large" class="card-img-top" alt="..." />
      <div class="card-body">
        <h5 class="card-title">{{ el.name.first }}</h5>
        <!-- <p class="card-text">
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </p>
        <a href="#" class="btn btn-primary">Go somewhere</a> -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    list: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style>
</style>