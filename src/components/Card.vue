<template>
  <div class="card-container">
    <div class="card-elements-container">
      <div class="card-header-container">
        <div class="picture-container">
          <img
            class="picture"
            :src="require(`../assets/${this.user.image.png}`)"
            alt="profile-image"
          />
        </div>
        <div class="username">{{ user.username }}</div>
        <div class="createdAt">{{ createdAt }}</div>
      </div>
      <div class="content-container">{{ content }}</div>
      <div class="score-container">{{ score }}</div>
      <div class="reply-btn-container">reply</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    id: Number,
    content: String,
    createdAt: String,
    score: Number,
    // optional
    replyingTo: String,
    user: {
      image: {
        png: String,
        webp: String,
      },
      username: String,
    },
    // optional
    replies: Array,
    type: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card-container {
  color: rgb(74, 23, 32);
  width: 100%;
  padding: 16px;
  /* border: 2px solid purple; */
}

.card-elements-container {
  /* border: 2px solid brown; */
  display: grid;
  grid-template-rows: 0.42fr 1.605fr 0.534fr;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.card-header-container {
  /* border: 2px solid green; */
  grid-column: span 2;
  display: flex;
  gap: 16px;
}

.picture-container {
  /* border: 1px solid black; */
  /* width: 32px;
  height: 32px; */
}
.picture {
  width: 32px;
  height: 32px;
}
.username {
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 500;
  line-height: 18.96px;
  color: #334253;
  /* border: 1px solid black; */
}

.createdAt {
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  color: #67727E;
  /* border: 1px solid black; */
}

.content-container {
  /* border: 2px solid red; */
  color: #67727E;
  text-align: left;
  grid-column: span 2;
}

.score-container {
  border: 2px solid blue;
}

.reply-btn-container {
  border: 2px solid purple;
}
</style>
