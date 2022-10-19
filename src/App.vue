<script setup>
import { RouterLink, RouterView } from "vue-router";
import NavBar from "./components/NavBar.vue";
</script>



<script>


</script>


<template>
  <header>
    
   <NavBar/>
  </header>
  <RouterView />
</template>


<style scoped>
body {
  margin: 0;
  background-color: #ffeedd;
  display: flex;
}
</style>