
<!-- App.vue nihel -->
<script setup>
import BCarousel from "../components/BCarousel.vue";
import Post from "../components/Post.vue"


</script>


<template>
  <main>

    <BCarousel />
  </main>
  <Post v-if="showPost" :post="post" @reload-postlist="getPosts"/>
</template>

<script >

</script>
