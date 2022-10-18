<script setup>
import { RouterLink, RouterView } from "vue-router";

</script>

<script>
export default {
  data() {
    return { isConnected: Boolean(localStorage.getItem("token")) };
  },
  mounted: function () {
    this.$router.afterEach(() => {
      // this.isConnected = !!localStorage.getItem("token");
      this.isConnected = Boolean(localStorage.getItem("token"));
    });
  }
}
</script>
<template>
  <header>
    <!-- <img alt="Vue logo" class="logo" src="@/assets/ChatMatchLogo.png" width="125" height="125" /> -->

    <div v-if="isConnected" class="wrapper">
      <nav>
        <RouterLink to="/"><video class="logo" src="@/assets/ChatMatchVideo.mp4" autoplay muted></video></RouterLink>
        <RouterLink class="hover-a" to="/createAccount">Créer un compte</RouterLink>
        <RouterLink class="hover-a" to="/login">Se connecter</RouterLink>
      </nav>
    </div>

  </header>

  <RouterView />
</template>

<style scoped>
body {
  margin: 0;
  background-color: #ffeedd;
  display: flex;
}

header {
  margin-top: 0;
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: flex;
  /* margin: 0 auto 2rem; */
  width: 250px;
  height: 250px;
}

nav {
  display: flex;
  align-items: center;
  justify-content: center;
  /* width: 100%; */
  font-size: 12px;
  text-align: center;
  margin-top: 1px;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    place-items: center;
    /* padding-right: calc(var(--section-gap) / 2); */
  }

  .logo {
    margin: 0 2rem 0 0;
    align-items: center;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
    margin-top: 0;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;
    margin-top: 0;
  }
}
</style>
