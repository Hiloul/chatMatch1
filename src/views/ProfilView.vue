<script>
import CreatePost from '../components/CreatePost.vue';
export default {
    data() {
        return {
            name: "",
            pseudo: "",
            email: "",
            password: "",
            result: true,
            token: "",
            showCreatePost: false
        };
    },
    methods: {
      togglePost (){
        this.showCreatePost = !this.showCreatePost
      },
        async register() {
            const options = {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                },
                body: JSON.stringify({
                    name: String,
                    pseudo: String,
                    email: String,
                    password: String,
                }),
            };
            const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/chat-match/profil", options);
            const data = await response.json();
            this.result = data.success;
            if (data.success === true) {
                this.token = data.token;
                localStorage.setItem("token", data.token);
                // voici comment lire une valeur stockée dans le disque dur
                this.token = localStorage.getItem("token");
                // voici comment vider le stockage du disque dur
                localStorage.clear();
            }
        },
    },
    components: { CreatePost }
};
</script>
-->
<template>
  <div class="card">
    <p class="photoProfil">
      <img src="" alt="" />
    </p>
    <p>@</p>
    <textarea cols="" rows="" placeholder="Ecrivez votre bio ici..."></textarea>
    <button @click="togglePost" id="inputCreatePost">Créer un post</button>
  </div>

  <CreatePost v-if="showCreatePost"/>

</template>

<style scoped>

#inputCreatePost{
  margin: 20px;
  padding: 10px;
  background-color: #fe8c0e;
  color: white;
  border: 0px;
  border-radius: 5px;
  font-size: 15px;
}
#inputCreatePost:hover{
  cursor: pointer;
  background-color: #f9ddbe;
  color: #fe8c0e;
  transition: all 0.2s;
}


h1 {
  text-align: center;
  padding: 5px;
  color: #fe8c0e;
}

.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: white;
  height: 340px;
  padding: 5px;
  box-shadow: 1px 1px 5px 1px lightgray;
  border-radius: 20px;
}

.photoProfil {
  background-color: white;
  height: 100px;
  width: 100px;
  padding: 5px;
  box-shadow: 0.5px 0.5px 2.5px 0.5px lightgray;
  border-radius: 100px;
}

img {
  border-image-width: initial;
  height: 100px;
  width: 100px;
  border-radius: 100px;
}

textarea {
  cursor: pointer;
  width: 300px;
  height: 100px;
  margin: 0;
  resize: none;
  background-color: white;
  border: 1px solid grey;
  outline: none;
  padding: 5px;
  box-shadow: 0.5px 0.5px 2.5px 0.5px lightgray;
  border-radius: 5px;
  font-family: Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  scroll-behavior: smooth;
}

p {
  font-size: larger;
  font-weight: 400;
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
