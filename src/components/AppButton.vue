<template>
  <button :class="`btn btn-${typeButton}`" v-on="$listeners">
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    typeButton: {
      type: String,
      default: "primary",
    },
    remove: {
      type: Function,
      default: () => {},
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
