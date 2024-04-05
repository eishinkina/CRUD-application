<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <MyButton @click="showDialog" style="margin: 15px 0;">Создать пост</MyButton>
    <MyDialog v-model:show="dialogVisible">
      <PostForm @createPost="createPost" />
    </MyDialog>

    <PostList :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";

export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [
        {
          id: 1,
          title: "Пост о JavaScript",
          body: "JavaScript универсальный язык программирования",
        },
        {
          id: 2,
          title: "Пост о Vue",
          body: "Vue - это прогрессивный фреймворк",
        },
        {
          id: 3,
          title: "Пост о React",
          body: "React - это библиотека для создания пользовательских интерфейсов",
        },
      ],
      title: "",
      body: "",
      dialogVisible: false,
    };
  },
  methods: {
    createPost(post) {
      post.id = Date.now();
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

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
</style>
