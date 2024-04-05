<template>
  <div class="app">
    <PostForm @createPost="createPost" />
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
    };
  },
  methods: {
    // createPost() {
    //   const newPost = {
    //     id: Date.now(),
    //     title: this.title,
    //     body: this.body,
    //   };
    //   this.posts.push(newPost);
    //   this.title = "";
    //   this.body = "";
    // },
    createPost(post) {
      post.id = Date.now();
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
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
