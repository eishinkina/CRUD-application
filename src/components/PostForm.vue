<template>
  <div>
    <form @submit.prevent="emitCreatePost">
      <h4>Создание поста</h4>
      <MyInput
        v-model="post.title"
        type="text"
        placeholder="Введите название поста"
      />
      <MyInput
        v-model="post.body"
        type="text"
        placeholder="Введите описание поста"
      />

      <MyButton class="btn" style="align-self: flex-end; margin-top: 15px"
        >Добавить пост</MyButton
      >
    </form>
  </div>
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
    emitCreatePost() {
      if (this.post.title && this.post.body) {
        this.$emit("createPost", {
          title: this.post.title,
          body: this.post.body,
        });
        this.post.title = "";
        this.post.body = "";
      }
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
