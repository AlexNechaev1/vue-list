<template>
  <div>
    <template v-for="(item, index) in list">
      <Item
        v-bind:key="index"
        :id="item.id"
        :index="index"
        :itemName="item.name"
        :itemDescription="item.description"
        v-on:onDelete="onDelete"
      />
    </template>
  </div>
</template>

<script>
import Item from "./Item.vue";

export default {
  name: "ListItem",
  props: {
    list: Array,
  },
  methods: {
    onDelete(index) {
      this.$emit("onDelete", index);
    },
  },
  components: {
    Item,
  },
};
</script>

<style scoped></style>
