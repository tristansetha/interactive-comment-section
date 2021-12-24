<template>
  <h1> </h1>
  <main class="main-container">
    <div class="comments-container">
      <Comment
        v-for="comment in comments"
        :key="comment.id"
        :currentUser="currentUser"
        :handleComment="handleComment"
        :handleDeletion="handleDeletion"
        v-bind:comment="comment"
      />
    </div>
    <CommentForm
      commentFormType="comment-new"
      :handleComment="handleComment"
      :currentUser="this.currentUser"
    />
  </main>
</template>

<script>
import json from "../data.json";
import Comment from "./views/Comment.vue";
import CommentForm from "./components/CommentForm.vue";
export default {
  name: "App",
  components: {
    Comment,
    CommentForm,
  },
  data: () => {
    return {
      Generate_ID: 5,
      currentUser: json.currentUser,
      comments: json.comments,
    };
  },
  methods: {
    handleDeletion(info) {
      if (info.type === "comment") {
        for (let i = 0; i < this.comments.length; i++) {
          if (this.comments[i].id === info.id) {
            this.comments.splice(i, 1);
            break;
          }
        }
      } else if (info.type === "reply") {
        for (let i = 0; i < this.comments.length; i++) {
          if (this.comments[i].id === info.threadId) {
            for (let j = 0; j < this.comments[i].replies.length; j++) {
              if (this.comments[i].replies[j].id === info.id) {
                this.comments[i].replies.splice(j, 1);
                console.log(this.comments[i].replies);
                break;
              }
            }
          }
        }
      }
    },
    handleComment(comment) {
      const commentType = comment.type;
      switch (commentType) {
        case "comment-new":
          this.comments.push({
            id: this.Generate_ID++,
            content: comment.commentInput,
            createdAt: "Today",
            score: 0,
            user: this.currentUser,
            replies: [],
          });
          break;
        case "comment-reply":
          for (const c of this.comments) {
            if (c.id === comment.threadId) {
              c.replies.push({
                id: this.Generate_ID++,
                content: comment.commentInput,
                createdAt: "Today",
                score: 0,
                replyingTo: comment.replyingTo,
                user: this.currentUser,
              });
            }
          }
          console.log(this.comments);
          break;
        case "reply-reply":
          for (const c of this.comments) {
            if (c.id === comment.threadId) {
              c.replies.push({
                id: this.Generate_ID++,
                content: comment.commentInput,
                createdAt: "Today",
                score: 0,
                replyingTo: comment.replyingTo,
                user: this.currentUser,
              });
            }
          }
          break;

        case "comment-update":
          for (let i = 0; i < this.comments.length; i++) {
            if (this.comments[i].id === comment.threadId) {
              this.comments[i].content = comment.commentInput;
              console.log(this.comments[i]);
              break;
            }
          }
          break;

        case "reply-update":
          for (let i = 0; i < this.comments.length; i++) {
            if (this.comments[i].id === comment.threadId) {
              for (let j = 0; j < this.comments[i].replies.length; j++) {
                if (this.comments[i].replies[j].id === comment.replyId) {
                  this.comments[i].replies[j].content = comment.commentInput;
                  break;
                }
              }
            }
          }

          break;
        default:
          console.log("no case");
          console.log(comment);
      }
    },
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

  --Mobile-breakpoint: 375px;
  --Desktop-breakpoint: 1440px;
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
  align-items: center;
  padding: 4% 2% 4% 2%;
}

.comments-container {
  width: 100%;
}
.comments-container > div:not(:first-child) {
  margin-top: 16px;
}

@media (min-width: 1440px) {
  .comments-container {
    width: 730px;
  }
}

#app {
  font-family: "Rubik", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: var(--Very-light-gray);
}
</style>
