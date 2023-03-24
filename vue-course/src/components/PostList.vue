<template>
  <div v-show="posts.length > 0">
    <h2>Users List</h2>

    <post-item
      :post="post"
      :key="post.id"
      v-for="post in posts"
      @remove="$emit('remove', post)"
    />
  </div>
  <div v-show="posts.length === 0">
    <h2 style="color: red">Users List is Empty</h2>
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
