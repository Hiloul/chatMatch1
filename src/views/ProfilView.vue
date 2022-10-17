<script>
export default {
  data() {
    return {
      name: "",
      pseudo: "",
      email: "",
      password: "",
      result: true,
      token: "",
    };
  },

  methods: {
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

      const response = await fetch(
        "https://social-network-api.osc-fr1.scalingo.io/chat-match/login",
        options
      );

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
};
</script>
<template>
  <div class="card">
    <h1>Mon Profil</h1>

    <p class="photoProfil">
      <img src="data:image/jpeg;base64,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" alt="">
    </p>

    <p>@</p>
    <p>Status:</p>
    <textarea cols="" rows="" placeholder="Ecrivez votre bio ici..."></textarea>

  </div>
</template>

<style>
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
  box-shadow: 2px 2px 10px 2px lightgray;
  border-radius: 20px;
}

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
  font-family: Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
    Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
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
  