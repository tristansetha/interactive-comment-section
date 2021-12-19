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
        <div class="username">
          <span>
            {{ user.username }}
          </span>
        </div>
        <div class="createdAt">
          <span>
            {{ createdAt }}
          </span>
        </div>
      </div>
      <div class="content-container">{{ content }}</div>
      <div class="score-container">
        <div class="score-btn">
          <button class="score-add-btn">
            <img :src="plusIcon" alt="add-score" />
          </button>
          <span class="score-data">
            <div>{{ score }}</div>
          </span>
          <button class="score-minus-btn">
            <img :src="minusIcon" alt="minus-score" />
          </button>
        </div>
      </div>
      <div class="reply-btn-container">
        <img :src="replyIcon" alt="reply icon" /> reply
      </div>
    </div>
  </div>
</template>

<script>
import PlusIcon from "../assets/images/icon-plus.svg";
import MinusIcon from "../assets/images/icon-minus.svg";
import ReplyIcon from "../assets/images/icon-reply.svg";
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
  data: function () {
    return {
      plusIcon: PlusIcon,
      minusIcon: MinusIcon,
      replyIcon: ReplyIcon,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card-container {
  color: rgb(74, 23, 32);
  width: 100%;
  padding: 16px;
  background-color: var(--White);
  border-radius: 8px;
}

.card-elements-container {
  display: grid;
  grid-template-rows: 0.42fr 1.605fr 0.534fr;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.card-header-container {
  grid-column: span 2;
  display: flex;
  align-items: center;
  gap: 16px;
}

.picture-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
.picture {
  width: 32px;
  height: 32px;
}

.username {
  height: 100%;
}
.username span {
  font-weight: 700;
  line-height: 18.96px;
  color: var(--Dark-blue);
}

.createdAt {
  height: 100%;
}

.createdAt span {
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  color: var(--Grayish-Blue);
  /* border: 1px solid black; */
}

.content-container {
  /* border: 2px solid red; */
  color: var(--Grayish-Blue);
  text-align: left;
  grid-column: span 2;
}

.score-btn {
  width: 100px;
  height: 40px;
  border-radius: 10px;
  background-color: var(--Very-light-gray);
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.score-add-btn {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
  border: none;
  background-color: var(--Very-light-gray);
}
.score-minus-btn {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
  border: none;
  background-color: var(--Very-light-gray);
}

.score-data {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 700;
  line-height: 18.96px;
  color: var(--Moderate-blue);
}

.reply-btn-container {
  display: flex;
  justify-content: right;
  align-items: center;
  gap: 8px;
  font-weight: 700;
  color: var(--Moderate-blue);
}
</style>
