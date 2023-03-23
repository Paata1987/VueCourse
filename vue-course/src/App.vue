<template>
  <div>
    <div>
      Amount of Likes <strong>{{ likes }}</strong>
    </div>
    <div>
      Amount of Dislikes <strong>{{ dislikes }}</strong>
    </div>
    <div>
      <button @:click="addLike">Like</button>
      <button @click="addDislikes">Dislike</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      likes: 0,
      dislikes: 0,
    };
  },
  methods: {
    addLike() {
      this.likes += 1;
    },
    addDislikes() {
      this.dislikes += 1;
    },
  },
};
</script>

<style></style>
