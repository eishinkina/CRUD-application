<template>
  <div class="app">
    <form @submit.prevent>
      <h4>Создание поста</h4>
      <input
        v-model="title"
        class="input"
        type="text"
        placeholder="Введите название поста"
      />
      <input
        v-model="body"
        class="input"
        placeholder="Введите описание поста"
      />
      <button class="btn" @click="createPost">Добавить пост</button>
    </form>
    <div class="post" v-for="post in posts" :key="post.id">
      <div><strong>Название: </strong>{{ post.title }}</div>
      <div><strong>Описание: </strong>{{ post.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
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

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
form {
  display: flex;
  flex-direction: column;
}
.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>
