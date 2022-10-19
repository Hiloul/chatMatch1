<script>
export default {
  props: ["post"],
  data() {
    return {
      credentials: "",
      pseudo: "",
      message: "",
      comment: "",
    };
  },

  methods: {

    async createComment(postId) {
      const token = localStorage.getItem("token");
      const options = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Authorization: "bearer " + token,
        },
        body: JSON.stringify({
          postId: postId,
          content: this.comment,
        }),
      };
      const response = await fetch(
        "https://social-network-api.osc-fr1.scalingo.io/chat-match/post/comment",
        options
      );

      const data = await response.json();
      console.log(data);
      this.$emit("reloadPostlist");
    },
  },
  async addLike(postId) {
    if (post.likes) {
      post.likes++;
    } else {
      post.likes = 1;
    }
    const token = localStorage.getItem("token");
    const options = {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Authorization: "bearer " + token,
      },
      body: JSON.stringify({
        postId: postId,
      }),
    };
    const response = await fetch(
      "https://social-network-api.osc-fr1.scalingo.io/chat-match/post/like",
      options
    );
    const data = await response.json();
      console.log(data);
  },
  emits: ["reloadPostlist"],
};
</script>

<template>
  <div class="card-post">
    <img src="@/assets/Chat_Match_1avatard.png" class="photoProfil" alt="">
    <h2>@{{ post.firstname }}</h2>
    <p>{{ post.content }}</p>
    <button v-on:click.prevent="(e) => addLike(post._id)">
      <i class="fa-regular fa-heart"></i>
    </button>
    <span
      >{{ post.likes ? post.likes : "0" }} like{{
        post.likes && post.likes > 1 ? "s" : ""
      }}</span
    >
    <div id="comments">
      <form v-on:submit.prevent="(e) => createComment(post._id)">
        <input
          class="inputComment"
          v-model="comment"
          type="text"
          placeholder="Laissez un commentaire"
        />
      </form>
      <div class="commentsList">
        <div class="comment" v-for="comment in post.comments" :key="post.id">
          {{ comment.content }}
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.photoProfil {
  background-color: transparent;
  height: 100px;
  width: 100px;
  padding: 5px;
}

img {
  height: 100%;
  width: 100%;
  border-radius: 100px;
}
.card-post {
  text-align: center;
  justify-content: center;
  align-items: center;
  display: flex;
  padding-top: 20px;
  margin-top: 20px;
  background-color: white;
  display: flex;
  flex-direction: column;
  border-radius: 20px;
  box-shadow: 1px 1px 5px 1px lightgray;
}
button {
  border: none;
  background-color: white;
  cursor: pointer;
}
.fa-heart {
  width: 30px;
  height: 30px;
  display: flex;
  border: none;
  justify-content: center;
  text-align: center;
  align-items: center;
  /* margin: 20px;
  padding: 10px; */
  color: #fe8c0e;
  border-radius: 5px;
  font-size: 15px;
  transition: all 0.3s ease-in-out;
}

.fa-heart:hover {
  cursor: pointer;
  color: #fe8c0e;
  transition: all 0.2s;
  background-color: #f9ddbe;
}

.inputComment {
  margin: 20px 0px;
  padding: 5px;
  border: lightgray solid 1px;
  border-radius: 5px;
  outline: none;
}
.comment {
  text-align: start;
  border: 2px #f9ddbe solid;
  padding: 5px;
  border-radius: 5px;
  margin-bottom: 10px;
}
</style>
