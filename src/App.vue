<template>
  <main class="main-container">
    <!-- <Card v-bind:comments="comments" msg="Welcome to Your Vue.js App" /> -->
    <div class="comments-container">
      
    </div>
    <Card
      v-for="comment in comments"
      :key="comment.id"
      :id="comment.id"
      :content="comment.content"
      :createdAt="comment.createdAt"
      :score="comment.score"
      :user="comment.user"
      :replies="comment.replies"
    />
  </main>
</template>

<script>
import Card from "./components/Card.vue";
import json from "../data.json";
export default {
  name: "App",
  components: {
    Card,
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
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main-container {
  display: flex;
  justify-content: center;
  align-content: center;
  padding: 4% 2% 4% 2%;
  border: 2px solid blue;
}

/* .card-container {
  border: 2px solid purple;
  width: 100%;
} */

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  border: 1px solid black;
}
</style>
