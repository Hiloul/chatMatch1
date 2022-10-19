<script>
export default {
  data() {
    return {
      lastname:"Coucou",
      email: "",
      password: "",
    };
  },
  mounted: function () {
    this.modifierProfil();
    
  },
  methods: {
    modifierProfil() {
      this.showModifierProfil = !this.showModifierProfil
    },
    async post() {
      const options = {
        method: "PUT",
        headers: {
          "Content-Type": "application/json",
          Authorization: "bearer token",
        },
        body: {
          firstname: String,
lastname: String,
email: String,
age: Number,
occupation: String
        },
      };

      const response = await fetch("https://social-network-api.osc-fr1.scalingo.io/chat-match/user",
        options)

      const modifyProfil = await response.json()
    },
  },
};
</script>

<template>

  <div id="card-post">
    <form>
  
      <input @submit="modifierProfil" type="submit" name="" id="inputModifier" value="Modifier">
    </form>
  </div>
</template>



<style scoped>
#inputModifier{
 padding: 2px;
 background-color: #fe8c0e;
 color: white;
 border: 0px;
 border-radius: 5px;
}

#inputModifier:hover {
 cursor: pointer;
 background-color: #f9ddbe;
 color: #fe8c0e;
 transition: all 0.2s;

}

</style>
