<script>
export default {
  data() {
    return {
      name: "coucouc",
      pseudo: "mioumiou",
      email: "test@test.com",
      password: "test",
      result: null,
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
      }
    },
  },
};
</script>

<template>
  <h1>Créer un compte</h1>

  <form @submit.prevent="register">
    <div class="input-container">
        
      <label for="nomInput"></label>
      <input placeholder="Nom/Prénom" id="nomInput" v-model="nom" required />

      <label for="pseudoInput"></label>
      <input
        type="text"
        id="pseudoInput"
        placeholder="Pseudo"
        v-model="pseudo"
        required
      />

      <label for="emailInput"></label>
      <input
        type="email"
        id="emailInput"
        placeholder="Mail"
        v-model="email"
        required
      />

      <label for="passwordInput"></label>
      <input
        type="password"
        id="passwordInput"
        placeholder="Password"
        v-model="password"
        required
      />
      <input class="createaccount-btn" type="submit" value="S'inscrire"/>
    </div>
  </form>
   
  <div class="input-container">
    <p v-if="result === true" class="success">
      Creation réussie
      <br />
      Token: {{ token }}
    </p>
    <p v-else-if="result === false" class="error">Creation échouée</p>
  </div>
</template>

<style scoped>
div {
  background-color: white;
  height: 340px;
  padding: 5px;
  box-shadow: 2px 2px 10px 2px lightgray;
  border-radius: 50px;
}

h1 {
  text-align: center;
  text-decoration: underline;
  padding: 5px;
  color: #fe8c0e;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1rem;

  text-align: center;
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

button {
  margin-left: 45%;
  padding: 10px;
  text-align: justify;
  border-radius: 10px;
  margin-top: 1rem;
  padding: 6px;
  border-radius: 8px;
  border: none;
  font-weight: 600;
  outline: none;
  background-color: #fe8c0e;
  color: white;
}

button:hover {
  background-color: #ffeedd;
  box-shadow: 1px 1px 5px 1px lightgray;
  color: #fe8c0e;
  transition: all 0.3s;
}
</style>
