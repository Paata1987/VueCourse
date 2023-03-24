<template>
  <div>
    <h3>Users List</h3>
    <post-item
      :post="post"
      :key="post.id"
      v-for="post in posts"
      @remove="$emit('remove', post)"
    />
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
