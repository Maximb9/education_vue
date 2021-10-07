<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "my-button",
};
</script>

<style scoped>
.btn {
  margin-top: 15px;
  background-color: hotpink;
  border: hotpink;
  padding: 10px;
  color: ivory;
}
</style>