<template>
  <main class="main-container">
    <div class="comments-container">
      <Comment
        v-for="comment in comments"
        :key="comment.id"
        :currentUser="currentUser"
        v-bind:comment="comment"
      />
    </div>
    <div class="comment-form-container">
      <div class="input-container">
        <textarea
          class="comment-input"
          name="comment"
          placeholder="Add a comment..."
        ></textarea>
      </div>
      <div class="picture-container">
        <img
          class="picture"
          :src="require(`./assets/${this.currentUser.image.png}`)"
          alt="profile picture"
        />
      </div>
      <div class="send-btn-container">
        <button class="send-btn">SEND</button>
      </div>
    </div>
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
  flex-direction: column;
  justify-content: center;
  align-content: center;
  padding: 4% 2% 4% 2%;
  /* border: 2px solid blue; */
}

.comments-container {
  /* border: 2px solid purple; */
  width: 100%;
}
.comments-container > div:not(:first-child) {
  margin-top: 16px;
}

.comment-form-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 0.5fr;
  gap: 16px;
  padding: 16px;
  margin-top: 16px;
  height: 189px;
  border-radius: 8px;
  /* border: 1px solid black; */
  background-color: var(--White);
}

.input-container {
  grid-column: span 2;
  /* border: 1px solid red; */
}

.comment-input {
  padding: 12px 24px 12px 24px;
  width: 100%;
  height: 100%;
  border: 1px solid var(--Light-gray);
  border-radius: 8px;
  font-family: "Rubik", sans-serif;
  font-weight: 500;
  color: var(--Grayish-Blue);
}

.comment-input:focus {
  outline: none !important;

  border: 1px solid var(--Moderate-blue);
}

.picture-container {
  display: flex;
  align-items: center;
  /* border: 1px solid black; */
}

.picture {
  width: 32px;
  height: 32px;
}

.send-btn-container {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  /* border: 1px solid black; */
}

.send-btn {
  height: 48px;
  width: 104px;
  border: none;
  border-radius: 8px;
  color: var(--White);
  background-color: var(--Moderate-blue);
  font-weight: 500;
  font-family: "Rubik", sans-serif;
}

.send-btn:hover {
  cursor: pointer;
  background-color: var(--Light-grayish-blue);
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
