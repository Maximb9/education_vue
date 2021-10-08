<template>
  <div class="app">
    <h1>Старница с постами</h1>
    <my-button @click="showDialog" style="margin: 15px 0px"
      >Создать пост</my-button
    >
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-dialog>
    <post-list :posts="posts" @remove="removePost" v-if="!isPostsLoading" />
    <div v-else>Идет загрузка...</div>
  </div>
</template>

<script>
// импорт компонентов
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyDialog from "./components/UI/MyDialog.vue";
import axios from "axios";
import MyButton from "./components/UI/MyButton.vue";
//  в эту секцию по дефолту мы должны экспортировать объект. По сути этот объект и будет являться компонентом
export default {
  // компонент необходимо зарегистрировать
  components: {
    PostForm,
    PostList,
    MyDialog,
    MyButton,
  },

  data() {
    return {
      // внутри мы можем объявлять поля (модели - likes)
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
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
    async fetchPosts() {
      try {
        this.isPostsLoading = true;

        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts?_limit=10"
        );
        this.posts = response.data;
      } catch (e) {
        alert("Ошибка");
      } finally {
        this.isPostsLoading = false;
      }
    },
  },
  // Динамическая подгрузка постов в хуке mounted
  mounted() {
    this.fetchPosts();
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
