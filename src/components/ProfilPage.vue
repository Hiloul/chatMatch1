<script>
export default {
  props: ["text", "status"],
};
</script>

<template>
  <div class="task">
    <p>{{ text }}</p>
    <p>{{ status }}</p>
  </div>
</template>

<style scoped>
.task {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 200px;
  height: 1.5rem;
}

p:first-child {
  color: red;
}
p:last-child {
  color: green;
}
</style>
