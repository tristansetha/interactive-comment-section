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
      :handleDeletion="handleDeletion"
      type="comment"
      :threadId="comment.id"
      :commentFormType="
        currentUser.username === comment.user.username
          ? 'comment-update'
          : 'comment-reply'
      "
    />
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
        :handleDeletion="handleDeletion"
        :threadId="comment.id"
        :commentFormType="
          currentUser.username === reply.user.username
            ? 'reply-update'
            : 'reply-reply'
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
    handleDeletion: Function,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.comment-container {
  color: rgb(74, 23, 32);
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.replies-container {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  margin-top: 16px;
  border-left: 2px solid var(--Light-gray);
}

.replies-container > :not(:first-child) {
  margin-top: 16px;
}

@media (min-width: 1440px) {
  .replies-container {
    width: 685px;
  }
}
</style>
