<template>
  <div :class="type === 'reply' ? 'reply-container' : 'card-container'">
    <div class="card-elements-container">
      <div class="card-header-container">
        <div class="picture-container">
          <img
            class="picture"
            :src="require(`../assets/${this.user.image.png}`)"
            alt="profile-image"
          />
        </div>
        <div class="username-container">
          <span class="username">
            {{ user.username }}
          </span>
        </div>
        <div v-if="currentUser.username === user.username" class="you-label">
          <span>you</span>
        </div>
        <div class="createdAt-container">
          <span>
            {{ createdAt }}
          </span>
        </div>
      </div>
      <div v-if="type === 'reply'" class="content-container">
        <span>@{{ replyingTo }} </span> {{ content }}
      </div>
      <div v-else class="content-container">
        {{ content }}
      </div>
      <div class="score-container">
        <div class="score-btn">
          <button @click="addScore()" class="score-add-btn">
            <img :src="plusIcon" alt="add-score" />
          </button>
          <span class="score-data">
            <div>{{ currentScore }}</div>
          </span>
          <button @click="minusScore()" class="score-minus-btn">
            <img :src="minusIcon" alt="minus-score" />
          </button>
        </div>
      </div>
      <div v-if="currentUser.username === user.username" class="edit-container">
        <div class="delete">
          <div>
            <img :src="deleteIcon" alt="delete comment" />
          </div>
          <span> Delete </span>
        </div>
        <div @click="this.replyFormOpen = !this.replyFormOpen" class="edit">
          <div>
            <img :src="editIcon" alt="edit comment" />
          </div>
          <span>Edit</span>
        </div>
      </div>
      <div
        @click="this.replyFormOpen = !this.replyFormOpen"
        v-else
        class="reply-btn-container"
      >
        <img class="reply-icon" :src="replyIcon" alt="reply icon" />
        <span>reply</span>
      </div>
    </div>
  </div>
  <CommentForm
    v-if="replyFormOpen"
    :commentId="commentFormCommentId"
    :replyingTo="user.username"
    :commentFormType="commentFormType"
    :handleComment="handleComment"
    :currentUser="currentUser"
  />
  <!-- <div>hello world</div> -->
</template>

<script>
import CommentForm from "../components/CommentForm.vue";
import PlusIcon from "../assets/images/icon-plus.svg";
import MinusIcon from "../assets/images/icon-minus.svg";
import ReplyIcon from "../assets/images/icon-reply.svg";
import DeleteIcon from "../assets/images/icon-delete.svg";
import EditIcon from "../assets/images/icon-edit.svg";
export default {
  name: "Card",
  components: {
    CommentForm,
  },
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
    currentUser: Object,
    type: String,
    handleComment: Function,
    commentFormType: String,
    commentFormCommentId: Number,
  },
  data: function () {
    return {
      replyFormOpen: false,
      currentScore: this.score,
      plusIcon: PlusIcon,
      minusIcon: MinusIcon,
      replyIcon: ReplyIcon,
      deleteIcon: DeleteIcon,
      editIcon: EditIcon,
    };
  },
  methods: {
    addScore() {
      this.currentScore++;
    },
    minusScore() {
      this.currentScore--;
    },
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
  /* border: 2px solid black; */
}
.reply-container {
  color: rgb(74, 23, 32);
  width: 94%;
  padding: 16px;
  background-color: var(--White);
  border-radius: 8px;
  /* border: 2px solid black; */
}

.card-elements-container {
  display: grid;
  grid-template-rows: 0.42fr 1.605fr 0.534fr;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.card-header-container {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  grid-column: span 2;
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

.you-label {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 36px;
  height: 19px;
  background-color: var(--Moderate-blue);
  color: var(--White);
  border-radius: 2px;
}

.you-label > span {
  font-weight: 500;
  font-size: 13px;
}

.username-container {
}
.username {
  font-weight: 700;
  color: var(--Dark-blue);
}

.createdAt-container {
  /* height: 100%; */
}

.createdAt-container > span {
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  color: var(--Grayish-Blue);
  /* border: 1px solid black; */
}

.content-container {
  /* border: 2px solid red; */
  font-weight: 500;
  color: var(--Grayish-Blue);
  text-align: left;
  grid-column: span 2;
}

.content-container > span {
  color: var(--Moderate-blue);
  font-weight: 500;
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

.edit-container {
  display: flex;
  justify-content: right;
  align-items: center;
  gap: 16px;
  font-weight: 700;
  /* color: var(--Moderate-blue); */
}
.edit-container .delete {
  display: flex;
  gap: 8px;
  cursor: pointer;
}
.edit-container .delete:hover {
  filter: opacity(25%);
}

.edit-container .delete > span {
  color: var(--Soft-Red);
}
.edit-container .edit {
  display: flex;
  gap: 8px;
  cursor: pointer;
}
.edit-container .edit:hover {
  filter: opacity(25%);
}
.edit-container .edit > span {
  color: var(--Moderate-blue);
}

.reply-btn-container {
  display: flex;
  justify-content: right;
  align-items: center;
  gap: 8px;
  font-weight: 700;
  color: var(--Moderate-blue);
  cursor: pointer;
}

.reply-btn-container:hover {
  filter: opacity(25%);
}
</style>
