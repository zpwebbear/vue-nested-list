<template functional>
  <li class="item">
    <slot></slot>
  </li>
</template>

<script>
export default {
  name: "custom-list-item"
};
</script>

<style scoped>
.item {
  text-align: left;
}
</style>


