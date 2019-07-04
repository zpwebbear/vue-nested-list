<template>
  <ul class="list">
    <custom-list-item v-for="item in items" :key="item.id">
      <full-list-item
        :item="item"
        @item:move-up="itemMoveUp(item.id)"
        @item:move-down="itemMoveUp(item.id)"
        @item:add-sublist="itemAddSublist(item.id)"
        @item:remove-sublist="itemRemoveSublist(item.id)"
        @item:remove="itemRemove(item.id)"
      />
    </custom-list-item>
    <custom-list-item>
      <empty-list-item @submit="itemAdd"/>
    </custom-list-item>
  </ul>
</template>

<script>
import CustomListItem from "./CustomListItem";
import FullListItem from "./FullListItem";
import EmptyListItem from "./EmptyListItem";
import cuid from "cuid";

export default {
  name: "custom-list",
  components: {
    CustomListItem,
    EmptyListItem,
    FullListItem
  },
  data() {
    return {
      items: []
    };
  },
  methods: {
    itemMoveUp(id) {
      console.log("id", id);
    },
    itemMoveDown(id) {
      console.log("id", id);
    },
    itemAddSublist(id) {
      this.items = this.items.map(item => {
        if (item.id === id) {
          return { ...item, hasSublist: true };
        }

        return item;
      });
    },
    itemRemoveSublist(id) {
      console.log("id", id);
    },
    itemRemove(id) {
      console.log("id", id);
    },
    itemAdd(item) {
      this.items.push(this.generateItem(item));
    },
    getMaxFieldOfArrayOfItems(items, field) {
      return Math.max(...items.map(item => item[field]), 0);
    },
    getLastItemsOrder(items) {
      return this.getMaxFieldOfArrayOfItems(items, "order");
    },
    generateItem(text) {
      return {
        id: cuid(),
        order: this.getLastItemsOrder(this.items) + 1,
        label: text,
        hasSublist: false
      };
    }
  }
};
</script>

<style scoped>
.list {
  list-style-type: disc;
  max-width: 500px;
}
</style>


