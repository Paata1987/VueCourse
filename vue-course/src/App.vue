<template>
  <div class="app">
    <h1>POSTS PAGE</h1>
    <div class="app__btns">
      <my-button @click="showDialog"> create user </my-button>
      <my-select v-model="selectedSort" :options="sortOptions" />
    </div>

    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-dialog>

    <post-list @remove="removePost" :posts="posts" v-if="!isPostsLoading" />
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import axios from "axios";
import MySelect from "./components/UI/MySelect.vue";

export default {
  components: {
    PostForm,
    PostList,
    MySelect,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPsotsLoading: false,
      selectedSort: "",
      sortOptions: [
        { value: "title", name: "By name" },
        { value: "body", name: "By descriprion" },
      ],
    };
  },
  methods: {
    createPost(post) {
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
        this.isPsotsLoading = true;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts?_limit=10"
        );
        this.posts = response.data;
        console.log(response);
        this.isPsotsLoading = false;
      } catch (error) {
        alert("error", error);
      } finally {
      }
    },
  },
  mounted() {
    this.fetchPosts();
  },
  computed: {
    sortedPosts() {
      return [...this.posts].sort((firstPst, secondPst) => {
        return firstPst[this.selectedSort]?.localeCompare(
          secondPst[this.selectedSort]
        );
      });
    },
  },
  /* watch: {
    selectedSort(newValue) {
      this.posts.sort((post1, post2) => {
        return post1[newValue]?.localeCompare(post2[newValue]);
      });
    },
  }, */
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
.app__btns {
  margin: 15px;
  display: flex;
  justify-content: space-between;
}
</style>
