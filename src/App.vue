<template>
  <main class="main-container">
    <!-- <Card v-bind:comments="comments" msg="Welcome to Your Vue.js App" /> -->
    <div class="comments-container">
      <Comment
        v-for="comment in comments"
        :key="comment.id"
        v-bind:comment="comment"
      />
    </div>
    <!-- <Card
      v-for="comment in comments"
      :key="comment.id"
      :id="comment.id"
      :content="comment.content"
      :createdAt="comment.createdAt"
      :score="comment.score"
      :user="comment.user"
      :replies="comment.replies" -->
    <!-- /> -->
  </main>
</template>

<script>
import json from "../data.json";
import Comment from "./views/Comment.vue";
export default {
  name: "App",
  components: {
    Comment,
  },
  data: () => {
    return {
      currentUser: json.currentUser,
      comments: json.comments,
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;700&display=swap");

:root {
  --Moderate-blue: hsl(238, 40%, 52%);
  --Soft-Red: hsl(358, 79%, 66%);
  --Light-grayish-blue: hsl(239, 57%, 85%);
  --Pale-red: hsl(357, 100%, 86%);

  --Dark-blue: hsl(212, 24%, 26%);
  --Grayish-Blue: hsl(211, 10%, 45%);
  --Light-gray: hsl(223, 19%, 93%);
  --Very-light-gray: hsl(228, 33%, 97%);
  --White: hsl(0, 0%, 100%);
}

html,
body {
  font-family: "Rubik", sans-serif;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 16px;
}

.main-container {
  display: flex;
  justify-content: center;
  align-content: center;
  padding: 4% 2% 4% 2%;
  /* border: 2px solid blue; */
}

.comments-container {
  /* border: 2px solid purple; */
  width: 100%;
}
.comments-container div:not(:first-child){
  margin-top: 16px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* border: 3px solid blue; */
  background-color: var(--Very-light-gray);

  min-height: 100vh;
}
</style>
