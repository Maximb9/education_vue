<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <input
      v-bind:value="title"
      @input="title = $event.target.value"
      class="input"
      type="text"
      placeholder="Название"
    />
    <input
      v-bind:value="body"
      @input="body = $event.target.value"
      class="input"
      type="text"
      placeholder="Описание"
    />
    <button class="btn">Создать</button>
  </form>
</template>

<script>
export default {};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}

.btn {
  align-self: flex-end;
  margin-top: 15px;
  background-color: hotpink;
  border: hotpink;
  padding: 10px;
  color: ivory;
}

.input {
  width: 100%;
  border: 1px solid green;
  padding: 10px;
  margin-top: 15px;
}
</style>