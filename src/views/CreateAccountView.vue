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
        "https://social-network-api.osc-fr1.scalingo.io/demo/register",
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

  computed: {
    
  }

};
</script>


<template>
  <form @submit.prevent="register">
    <h1>Créer un compte</h1>
    <div class="input-container">
      <label for="nom"></label>
      <input placeholder="Nom/Prénom" id="nomInput" v-model="nom" required />
    </div>
    <div class="input-container">
      <label for="pseudo"></label>
      <input type="text" id="pseudoInput" placeholder="Pseudo" v-model="pseudo" required />
    </div>
    <div class="input-container">
      <label for="email"></label>
      <input type="email" id="emailInput" placeholder="Email" v-model="email" required />
    </div>
    <div class="input-container">
      <label for="password"></label>
      <input type="password" :class="password" id="passwordInput" placeholder="Password" v-model="password"
        required />
    </div>
    <input class="createaccount-btn" type="submit" value="S'inscrire" />
  </form>
  

  <div class="input-container">
    <RouterLink to="/profil">
    <p v-if="result === false" class="success">
      Creation réussie
      <!-- <br />
      {{ token }} -->
      

    </p>
  </RouterLink>

  </div>
</template>

<style scoped>


form {
  display: flex;
  flex-direction: column;
  background-color: white;
  height: 340px;
  padding: 5px;
  box-shadow: 2px 2px 10px 2px lightgray;
  border-radius: 20px;
}

.input-container {
  margin: 10px;
  display: flex;
  flex-direction: row;
}

.input-container input {
  border: 1px solid grey;
  padding: 5px;
  font-size: 12px;
  border-radius: 5px;
  flex-grow: 1;
}

.createaccount-btn {
  margin-right: 25%;
  align-self: center;
  width: 100px;
  text-align: center;
  padding: 10px;
  background-color: #fe8c0e;
  color: white;
  border: 0px;
  border-radius: 5px;
  font-size: 15px;
}

.createaccount-btn:hover {
  cursor: pointer;
  background-color: #ffeedd;
  box-shadow: 1px 1px 5px 1px lightgray;
  color: #fe8c0e;
  transition: all 0.3s;
}

p.success {
  margin-top: 20px;
  width: 600px;
  text-align: center;
  font-weight: 500;
  border-radius: 5px;
  background-color: rgb(5, 150, 10);
  box-shadow: 1px 1px 5px 1px lightgray;
  color: white;
}

h1 {
  text-align: center;
  padding: 5px;
  color: #fe8c0e;
}

input {
  margin-left: 25%;
  padding: 10px;
  text-align: justify;
  border-radius: 10px;
  margin-top: 0.25rem;

  padding: 6px;
  border-radius: 8px;
  border: 1px solid rgb(217, 216, 216);
  box-shadow: 1px 1px 5px 1px lightgray;
  outline: none;
  max-width: 50%;
}
</style>
