<template>
  <div id="mainContainer">
    <div class="h2-style">
      <h2>Nous sommes heureux de vous revoir</h2>
    </div>
    <!-- Formulaire de login -->
    <form @submit.prevent="login" class="form-style">
      <div class="input-container">
        <input
          type="email"
          id="emailInput"
          v-model="email"
          placeholder="chatmatch@lebocal.academy"
          required
        />
      </div>

      <div class="input-container">
        <input
          type="password"
          id="passwordInput"
          v-model="password"
          placeholder="********"
          required
        />
      </div>
      <div v-if="result" class="input-container">
        <RouterLink to="/profil">
          <p v-if="result === true" class="success">Connexion réussie</p>
        </RouterLink>
      </div>
      <p v-else-if="result === false" class="error">
        Adresse mail ou mot de passe est invalide.
      </p>
    
      <input class="login-button" type="submit" value="Se connecter" />
      
    </form>
  </div>
  
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      result: null,
      token: "",
    };
  },

  methods: {
    async login() {
      const options = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          email: this.email,
          password: this.password,
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
        // rediriger vers la page d'accueil ?
        // voici comment "persister" une valeur dans le disque dur
        localStorage.setItem("token", data.token);
        // voici comment lire une valeur stockée dans le disque dur
        // const token = localStorage.getItem("token");
        // voici comment vider le stockage du disque dur
        // localStorage.clear();
        // console.log(localStorage);
        this.$router.push('/profil')
      }
    },
  },
};
</script>

<style scoped>
#mainContainer {
  display: flex;
  flex-direction: column;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  padding-top: 30px;
  background-color: white;
  border-radius: 20px;
  margin-bottom: 20px;
  box-shadow: 1px 1px 5px 1px lightgray;
  align-items: center;
}

.h2-style {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #fe8c0e;
  width: 400px;
  color: white;
  border-radius: 20px;
  text-align: center;
  font-size: 11px;
}

.input-container {
  padding-top: 20px;
  margin: 10px;
  display: flex;
  flex-direction: row;
  
}

.input-container input {
  border: 1px solid rgb(217, 216, 216);
  padding: 5px;
  font-size: 14px;
  border-radius: 5px;
  flex-grow: 1;
  width: 400px;
  height: 30px;
  outline:none ;
}

.login-button {
  margin: 20px;
  padding: 10px;
  background-color: #fe8c0e;
  color: white;
  border: 0px;
  border-radius: 5px;
  font-size: 15px;
}

.login-button:hover {
  cursor: pointer;
  background-color: #f9ddbe;
  color: #fe8c0e;
  transition: all 0.2s;
}

.success {
  margin-top: 20px;
  padding: 10px;
  background-color: #2c962c;
  color: white;
}

.error {
  margin-top: 20px;
  padding: 10px;
  /* background-color: #b42f26;
  color: white; */
  color: #b42f26;
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
