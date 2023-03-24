<template>
  <div>
    <h3>Users List</h3>
    <post-item :key="post.id" :post="post" v-for="post in posts" />
  </div>
</template>

<script>
import PostItem from "./PostItem.vue";
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style></style>
