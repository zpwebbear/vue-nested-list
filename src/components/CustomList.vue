<template>
  <ul class="list">
    <custom-list-item v-for="item in items" :key="item.id">
      <full-list-item :item="item" @item:move-up="moveItemUp(item.id)"/>
    </custom-list-item>
    <custom-list-item>
      <empty-list-item @submit="addItem"/>
    </custom-list-item>
  </ul>
</template>

<script>
import CustomListItem from "./CustomListItem.vue";
import FullListItem from "./FullListItem.vue";
import EmptyListItem from "./EmptyListItem.vue";
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
  computed: {
    itemListeners($event, id) {
      console.log($event, id);
      var vm = this;
      return Object.assign({}, this.$listeners, {
        input: function(event) {
          vm.$emit("input", event.target.value);
        }
      });
    }
  },
  methods: {
    moveItemUp(id) {
      console.log("id", id);
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
    },
    addItem(item) {
      this.items.push(this.generateItem(item));
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


