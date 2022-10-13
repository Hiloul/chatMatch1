<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1 class="orange">{{ msg }}</h1>
    <h3>
      Le premier réseau social pour chats
    </h3>
  </div>
</template>

<style scoped>

h1 {
  display: flex;
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
  justify-content: center;
  align-items: center;
}

h3 {
  font-size: 1.2rem;
  align-items: center;
  justify-content: center;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: center;
  }
}
</style>
