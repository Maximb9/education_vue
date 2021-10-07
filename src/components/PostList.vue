<template>
  <div class="post" v-for="post in posts">
    <div><strong>Название</strong> {{ post.title }}</div>
    <div><strong>Описание</strong> {{ post.body }}</div>
  </div>
</template>

<script>
export default {
  props: {
    // указываем, то что мы ожидаем на вход. В данном случае посты.
    // указываем тип, в данном случаи массив
    // чем будут инициализироваться
    // можно сделать их обязательными required: true
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.post {
  padding: 15px;
  border: 3px solid green;
  margin-top: 15px;
}
</style>