<template functional>
  <FullListItem v-if="props.item.id"/>
  <EmptyListItem v-else/>
</template>

<script>
import FullListItem from "./FullListItem";
import EmptyListItem from "./EmptyListItem";

export default {
  name: "CustomListItem",
  props: {
    item: {
      type: Object,
      default() {
        return {};
      }
    }
  }
};
</script>

<style scoped>
.item {
  color: black;
}
</style>


