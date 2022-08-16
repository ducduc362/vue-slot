<template>
  <div class="row">
    <div class="col-4 p-4" v-for="item in list" :key="item.email">
      <img :src="item.picture.large" class="card-img-top" alt="..." />
      <div class="card-body">
        <slot name="first" :item="item" :text="item.name.first"></slot>
        <slot name="last" :item="item" :text="item.name.last"></slot>
        <slot
          name="full"
          :item="item"
          :text="`${item.name.first} ${item.name.last}`"
        ></slot>
        <slot
          name="fullWidthTitle"
          :item="item"
          :text="`${item.name.title} ${item.name.first} ${item.name.last}`"
        ></slot>
        <slot name="secondrow" :item="item"></slot>
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