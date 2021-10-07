<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <input
      v-model="post.title"
      class="input"
      type="text"
      placeholder="Название"
    />
    <input
      v-model="post.body"
      class="input"
      type="text"
      placeholder="Описание"
    />
    <button class="btn" @click="createPost">Создать</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      //   Для того чтобы сгенерировать событие на которое родительский компонент может подписаться во vue есть специальная функция emit()
      //  первый параметр название события которое мы генерируем
      // вторым и последующими параметрами мы передаем аргументы которые будут попадать в соответствующую функцию,
      // после того, как на нее подпишется родительский компонент,
      // в данном случае передаем новый созданный пост
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
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