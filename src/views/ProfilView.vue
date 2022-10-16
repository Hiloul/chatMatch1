<script>
import ProfilPage from "./components/ProfilPage.vue";

export default {
  data() {
    return {
      newProfil: "",
      profilList: [],
    };
  },
  methods: {
    addProfil: function () {
      if (this.newProfil === "") {
        return;
      }
      const newProfil= {
        text: this.newProfil,
        status: "Profil",
      };
      this.profilList.push(newProfil);
      this.newProfil = "";
    },
  },
  components: {
    
    ProfilPage
},
};
</script>
<template>
  <h1>Ma todolist en Vue.JS</h1>
  <label>
    Veuillez saisir la prochaine tache à effectuer
    <input type="text" v-model="newProfil" />
    <button @click="addProfil">Ajouter</button>
  </label>
  <div>
    <ProfilPage
      v-for="profil in profilList"
      :text="profil.text"
      :status="profil.status"
      :key="profil.text"
    />
  </div>
</template>
  
  
  <style>
  @media (min-width: 1024px) {
    .about {
      min-height: 100vh;
      display: flex;
      align-items: center;
    }
  }
  </style>
  