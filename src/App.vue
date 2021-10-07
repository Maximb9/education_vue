<template>
  <div class="app">
    <post-form @create="createPost" />
    <post-list :posts="posts" />
  </div>
</template>

<script>
// импорт компонентов
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

//  в эту секцию по дефолту мы должны экспортировать объект. По сути этот объект и будет являться компонентом
export default {
  // компонент необходимо зарегистрировать
  components: {
    PostForm,
    PostList,
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
    };
  },
  //   функции объявляются в поле methods у компонента
  methods: {
    createPost(post) {
      this.posts.push(post);
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
