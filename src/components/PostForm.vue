<template>
  <div>
    <form @submit.prevent="emitCreatePost">
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
        type="text"
        placeholder="Введите описание поста"
      />

      <button class="btn">Добавить пост</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      body: "",
    };
  },
  methods: {
    emitCreatePost() {
      if (this.title && this.body) {
        // Добавлена простая проверка на пустые поля
        this.$emit("createPost", { title: this.title, body: this.body });
        this.title = "";
        this.body = "";
      }
    },
  },
};
</script>

<style scoped>
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
