<template>
  <div class="app">
    <post-form @create="createPost" />
    <post-list :posts="posts" />
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
    w;
  },
  methods: {
    createPost(first, second, third) {
      console.log(first, second, third);
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
