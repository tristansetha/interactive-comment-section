<template>
  <div class="card-container">
    <div class="comment">
      {{ id }}
    </div>
    <!-- <div class="replies-container">
      <div v-for="reply in replies" :key="reply.id" class="reply">
        {{ reply.id }}
      </div>
    </div> -->
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
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
  border: 2px solid red;
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
