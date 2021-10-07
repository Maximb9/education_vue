<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <my-input v-model="post.title" type="text" placeholder="Название" />
    <my-input v-model="post.body" type="text" placeholder="Описание" />
    <my-button @click="createPost" style="align-self: self-end"
      >Создать</my-button
    >
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
</style>