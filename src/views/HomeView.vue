
<!-- App.vue nihel -->
<script setup>
import BCarousel from "../components/BCarousel.vue";
import Post from "../components/Post.vue"
</script>

<script>
export default{
components:{Post},
}
</script>

<template>
  <main>

    <BCarousel />
  
  </main>
  <Post v-if="showPost" :post="post" @reload-postlist="getPosts"/>

  <footer>
    <p>&copy; chatMatch</p>
  </footer>
</template>

<script >

</script>
<style scoped>
p{text-align: center;
font-family:  Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;;}
</style>
