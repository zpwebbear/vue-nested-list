<template>
  <div class="item">
    <span class="item__label">{{item.label}}</span>
    <div class="item__controls">
      <button @click.prevent="$emit('item:move-up')">&uarr;</button>
      <button @click.prevent="$emit('item:move-down')">&darr;</button>
      <button @click.prevent="$emit('item:add-sublist')">Add sublist</button>
      <button @click.prevent="$emit('item:remove-sublist')">Remove sublist</button>
      <button @click.prevent="$emit('item:remove')">x</button>
    </div>
    <custom-list/>
  </div>
</template>

<script>
import CustomList from "@/components/CustomList";

export default {
  name: "full-list-item",
  components: {
    CustomList
  },
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  data() {
    return {};
  },
  updated() {
    console.log("FULL LIST ITEM UPDATED", this.item);
  }
};
</script>

<style scoped>
.item {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
}
.item__label {
  display: inline-block;
  width: 200px;
}
.item__controls {
  margin-left: auto;
}
</style>


