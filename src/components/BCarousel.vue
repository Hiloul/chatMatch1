
<script setup>
import Card from "./Card.vue"
</script>

<template>
    <div id="cage">
        <button @click="previous">Prev</button>
        <template v-for="(profile, i) in profiles" :key="i">
            <section v-if="i === currentIndex" :class="`hero is-medium is-`">
                <div class="hero-body has-text-centered">
                    <Card :pseudo="profile.firstname" :description="profile.description" :img="profile.image" />
                </div>
            </section>

        </template>
        <button @click="previous">NEXT</button>
    </div>
</template>

<script>

export default {
    data() {
        return {
            profiles: [
                {
                    _id: 1, firstname: "Simba", image: "/photoChat/pexels-kelvin-valerio-617278.jpg", description: "Chomage"
                }, {
                    _id: 2, firstname: "Taj", image: "/photoChat/pexels-pixabay-208984.jpg", description: "En couple"
                }, {
                    _id: 3, firstname: "Meno", image: "/photoChat/pexels-nihat-68594.jpg", description: "Célib"
                }
            ],
            currentIndex: 0,
        }
    },
    methods: {
        previous: function () {
            if (this.currentIndex === 0) {
                this.currentIndex = this.profiles.length - 1;
            } else {
                this.currentIndex -= 1;
            }
        },
        next: function () {
            if (this.currentIndex === this.profiles.length - 1) {
                this.currentIndex = 0;
            } else {
                this.currentIndex += 1;
            }
        }
    }
}
</script>

<style scoped>
#cage {
    display: flex;
    flex-direction: row;
    align-items: center;
}

button {
    border-radius: 50px;
    height: 50px;
    width: 50px;
    border: none;
    margin: 20px;
    background-color: #fe8c0e;
    color: white;
}

button:hover {
    cursor: pointer;
    background-color: #ffeedd;
    box-shadow: 1px 1px 5px 1px lightgray;
    color: #fe8c0e;
    transition: all 0.3s;
}
</style>