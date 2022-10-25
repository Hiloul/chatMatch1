
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
  <div class="posts-container">
    <template v-for="post in postsList" :key="post.id" >
    <Post v-if="post.userId == profile._id" :post="post" @reload-postlist="getPosts"/>
  </template>
  </div>
</template>

<script >

</script>
