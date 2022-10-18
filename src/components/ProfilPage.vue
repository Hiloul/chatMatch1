<template>
  <vue-profile 
  nickname="@Lukenoutte" 
  bodyPhrase="Follow the white rabbit."
  :socialLinks="myLinks"
  :profileImg="Img"
  />
</template>

<script>
import Img from "../assets/img.png";
export default {
  data(){
    return{
      myLinks: { 
        git: "https://github.com/Lukenoutte",         
        link: "https://github.com/Lukenoutte/vue-profile", 
        },
        Img
    }
  }
}
</script>