<template>
  <div class="app">
    <div>
      <form @submit.prevent>
        <h4>create post</h4>
        <input
          v-bind:value="title"
          @input="title = $event.target.value"
          class="input"
          type="text"
          placeholder="title"
        />
        <input
          v-bind:value="body"
          @input="body = $event.target.value"
          class="input"
          type="text"
          placeholder="post"
        />
        <button class="btn" @click="createPost">create</button>
      </form>
    </div>
    <div class="post" v-for="post in posts">
      <div><strong>Title: </strong> {{ post.title }}</div>
      <div><strong>DEscription: </strong> {{ post.body }}</div>
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
          title: "javascript",
          body: "Lorem ipsum dolor sit amet consecteturadipisicing elit",
        },
        {
          id: 2,
          title: "javascript",
          body: "Lorem ipsum dolot consecteturadipisicing elit",
        },
        {
          id: 3,
          title: "javascript",
          body: "Lorem ipsum dolor sit amet co elit",
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
.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
.input {
  width: 100%;
  border: 2px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
</style>
