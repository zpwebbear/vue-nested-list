<template>
  <form @submit="handleSubmit" class="form">
    <input type="text" v-model="value" class="input">
    <div class="item__controls">
      <button type="submit">Add</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "empty-list-item",
  props: {},
  data() {
    return {
      value: ""
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.$emit("submit", this.value);
      this.value = "";
    }
  }
};
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
}
.input {
  display: inline-block;
  width: 100%;
}
.item__controls {
  margin-left: auto;
}
</style>


