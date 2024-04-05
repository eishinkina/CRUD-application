<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <MyButton @click="showDialog" style="margin: 15px 0">Создать пост</MyButton>
    <MyDialog v-model:show="dialogVisible">
      <PostForm @createPost="createPost" />
    </MyDialog>

    <PostList :posts="posts" @remove="removePost" v-if="!isPostLoading" />
    <div v-else>Идет загрузка...</div>
  </div>
</template>

<script>
import axios from "axios";
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";

export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [],
      title: "",
      body: "",
      dialogVisible: false,
      isPostLoading: false,
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
    async fetchPosts() {
      try {
        this.isPostLoading = true;
        setTimeout(async () => {
          const response = await axios.get(
            "https://jsonplaceholder.typicode.com/posts?_limit=10"
          );
          this.posts = response.data;
        }, 1000);
      } catch (e) {
        console.error(e);
      } finally {
        this.isPostLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPosts();
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
