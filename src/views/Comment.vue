<template>
  <div class="comment-container">
    <Card
      :id="comment.id"
      :content="comment.content"
      :createdAt="comment.createdAt"
      :score="comment.score"
      :user="comment.user"
      :currentUser="currentUser"
      :handleComment="handleComment"
      type="comment"
      :commentFormCommentId="comment.id"
      :commentFormType="
        currentUser.username === comment.user ? 'comment-update': 'comment-reply'"/>
    <div class="replies-container" v-if="comment.replies.length > 0">
      <Card
        v-for="reply in comment.replies"
        :key="reply.id"
        :id="reply.id"
        :content="reply.content"
        :createdAt="reply.createdAt"
        :replyingTo="reply.replyingTo"
        :score="reply.score"
        :user="reply.user"
        :currentUser="currentUser"
        :handleComment="handleComment"
        :commentFormCommentId="comment.id"
        :commentFormType="
          currentUser.username === comment.user ? 'reply-update' : 'reply-reply'
        "
        type="reply"
      />
    </div>
  </div>
</template>

<script>
import Card from "../components/Card.vue";
export default {
  name: "Comment",
  components: {
    Card,
  },
  props: {
    currentUser: Object,
    comment: Object,
    handleComment: Function,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.comment-container {
  color: rgb(74, 23, 32);
  width: 100%;
  /* gap: 16px; */
}

.replies-container {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  margin-top: 16px;
  border-left: 2px solid var(--Light-gray);
  /* border: 2px solid black; */
}

.replies-container > :not(:first-child) {
  margin-top: 16px;
  /* border: 10px solid blue; */
}

.comment {
  border: 2px solid black;
}
/* h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
} */
</style>
