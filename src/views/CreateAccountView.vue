<script>
export default {
  data() {
    return {
      name: "",
      pseudo: "",
      email: "",
      password: "",
      result: false,
    };
  },
  computed: {
    validPassword: function () {
      if (this.password.length < 4) return false;
      return true;
    },
  },
  methods: {
    async register() {
      const options = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          firstname: this.pseudo,
          lastname: this.name,
          email: this.email,
          password: this.password,
        }),
      };

      const response = await fetch(
        "https://social-network-api.osc-fr1.scalingo.io/chat-match/register",
        options
      );
      const data = await response.json();
      this.result = data.success;

      this.$router.push('/login')
    },
  },
};
</script>

<template>
  <form @submit.prevent="register">
    <h1>Créer un compte</h1>
    <div class="input-container">
      <label for="nom"></label>
      <input placeholder="Nom" id="nomInput" v-model="name" required />
    </div>
    <div class="input-container">
      <label for="pseudo"></label>
      <input
        type="text"
        id="pseudoInput"
        placeholder="Pseudo"
        v-model="pseudo"
        required
      />
    </div>
    <div class="input-container">
      <label for="email"></label>
      <input
        type="email"
        id="emailInput"
        placeholder="Email"
        v-model="email"
        required
      />
    </div>
    <div class="input-container">
      <label for="password"></label>
      <input
        type="password"
        :class="password"
        id="passwordInput"
        placeholder="Password"
        v-model="password"
        required
      />
    </div>
    <input class="createaccount-btn" type="submit" value="S'inscrire" />
  </form>

  <div v-if="result" class="input-container">
    <RouterLink to="/login"></RouterLink>
  </div>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  background-color: white;
  height: 340px;
  padding: 5px;
  box-shadow: 1px 1px 5px 1px lightgray;
  border-radius: 20px;
}

.input-container {
  margin: 10px;
  display: flex;
  flex-direction: row;
}

.input-container input {
  border: 1px solid rgb(217, 216, 216);
  padding-top: 5px;
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
  transition: all 0.2s;
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
