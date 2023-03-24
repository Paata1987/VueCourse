<template>
  <div>
    <form @submit.prevent>
      <h4>create post</h4>
      <input
        v-model="post.title"
        class="input"
        type="text"
        placeholder="title"
      />
      <input v-model="post.body" class="input" type="text" placeholder="post" />
      <button class="btn" @click="createPost">create</button>
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
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post, "second params", "third params ");
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
.btn {
  align-self: flex-end;
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 2px solid teal;
}

.input {
  width: 100%;
  border: 2px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
</style>
