<script setup>
import BCarousel from "./BCarousel.vue"
import Card from "./Card.vue"
</script>

<script>
export default {
    data() {
        return {
            commented: "",
            comments: []
        };
    },
    methods: {
        setNewCommented: function (event) {
            this.commented = event.target.value;
        },
        clickBtn: function () {
            if (!this.commented) return;
            this.comments.push(this.commented)
        }
    },
};
</script>


<!-- <template>
    
    <div class="row">
        <ul>
            <li v-for="text in comments">
                {{ text }}
            </li>
        </ul>
    </div>
    <div class="section">
        <div class="comment">
            <div class="image">
            </div>
            <input :value="commented" @input="setNewCommented" type="text" name="post" placeholder="Commented">
            <button @click="clickBtn"><i class="fa-regular fa-comment"></i> </button>
        </div>

    </div>
    
</template> -->


<template>
    <div class="contenaire">
        <div v-for="text in comments" class="row">
            <div class="img">
                <img src="../assets/photoChat/pexels-kelvin-valerio-617278.jpg" />
               
            </div>
              <div class="content">
                {{ text }}
                </div>
        </div>
    </div>

    <div class="input">
    <input :value="commented" @input="setNewCommented" type="text" name="post" placeholder="Commented">
    <button @click="clickBtn"><i class="fa-regular fa-comment"></i> </button>
</div>

</template>

<style scoped  >
.contenaire {
    width: 60%;
    
  height: 150px;
    background-color: #f3ae5f;
    overflow: hidden;
    overflow-y: scroll;
  scrollbar-width:initial;
  background-color: #fff;

}

.img {
    height: 10px;
    width: 10%;

}

img {
    height: auto;
    width: 100%;
    object-fit: cover;
    border-radius: 50%;
    border: 3px solid #fff;

}

.row {

    width: 60%;
    height: 100px;
    box-shadow: 0 0 7px #333;
    border-radius: 10px;
    display: flex;
    flex-direction: row;
    align-items:baseline;
    align-content: space-between;
    margin: 10px;
    background-color: #f3ae5f;
    

   
    
}

.fa-paw-simple {
    height: 5%;
    background-color: #f3ae5f;
}

.input{
    background-color: aqua;
    width: 60%;
    height: 50px;
    display: flex;
    justify-content: flex-end;
}

.content{
   color: #fff;
}
</style>