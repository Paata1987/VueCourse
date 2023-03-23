<template>
  <div>
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

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
</style>
