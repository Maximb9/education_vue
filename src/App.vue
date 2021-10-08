<template>
  <div class="app">
    <h1>Старница с постами</h1>
    <my-button @click="showDialog" style="margin: 15px 0px"
      >Создать пост</my-button
    >
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-dialog>
    <post-list :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
// импорт компонентов
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyDialog from "./components/UI/MyDialog.vue";

//  в эту секцию по дефолту мы должны экспортировать объект. По сути этот объект и будет являться компонентом
export default {
  // компонент необходимо зарегистрировать
  components: {
    PostForm,
    PostList,
    MyDialog,
  },

  data() {
    return {
      // внутри мы можем объявлять поля (модели - likes)
      posts: [
        { id: 1, title: "Js_1", body: "Описание_1" },
        { id: 2, title: "Js_2", body: "Описание_2" },
        { id: 3, title: "Js_3", body: "Описание_3" },
        { id: 4, title: "Js_4", body: "Описание_4" },
      ],
      dialogVisible: false,
    };
  },
  //   функции объявляются в поле methods у компонента
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
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
</style>>
