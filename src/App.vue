<template>
  <div class="app">
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
      <button class="btn" @click="createPost">Создать</button>
    </form>
    <div class="post" v-for="post in posts">
      <div><strong>Название</strong> {{ post.title }}</div>
      <div><strong>Описание</strong> {{ post.body }}</div>
    </div>
  </div>
</template>

<script>
//  в эту секцию по дефолту мы должны экспортировать объект. По сути этот объект и будет являться компонентом
export default {
  // внутри мы можем объявлять поля (модели - likes)
  data() {
    return {
      posts: [
        { id: 1, title: "Js_1", body: "Описание_1" },
        { id: 2, title: "Js_2", body: "Описание_2" },
        { id: 3, title: "Js_3", body: "Описание_3" },
        { id: 4, title: "Js_4", body: "Описание_4" },
      ],
      title: "",
      body: "",
    };
  },
  //   функции объявляются в поле methods у компонента
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      };
      this.posts.push(newPost);
      this.title = "";
      this.body = "";
    },
  },
};
</script>



// scoped стили будут применены только к этому компоненту и не будут доступны из вне
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
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

.post {
  padding: 15px;
  border: 3px solid green;
  margin-top: 15px;
}

.input {
  width: 100%;
  border: 1px solid green;
  padding: 10px;
  margin-top: 15px;
}
</style>>
