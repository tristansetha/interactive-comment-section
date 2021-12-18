<template>
  <div class="comment-container">
    <Card
      :id="comment.id"
      :content="comment.content"
      :createdAt="comment.createdAt"
      :score="comment.score"
      :user="comment.user"
      type="comment"
    />
    <!-- <div class="replies-container" v-if="comment.replies.length > 0">
      <Card
        v-for="reply in comment.replies"
        :key="reply.id"
        :id="reply.id"
        :content="reply.content"
        :createdAt="reply.createdAt"
        :score="reply.score"
        :user="reply.user"
        type="reply"
      />
    </div> -->
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
    comment: Object,
    // id: Number,
    // content: String,
    // createdAt: String,
    // score: Number,
    // user: {
    //   image: {
    //     png: String,
    //     webp: String,
    //   },
    //   username: String,
    // },
    // replies: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card-container {
  color: rgb(74, 23, 32);
  /* border: 2px solid red; */
  width: 100%;
  /* width: 91%; */
  /* height: 250px; */
}
.comment {
  border: 2px solid black;
}
h3 {
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
}
</style>
