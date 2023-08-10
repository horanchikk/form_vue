<template>
  <button>
    <slot />
  </button>
</template>

<script setup>
const props = defineProps({
  text: String,
});
</script>

<style scoped>
button {
  color: black;
  padding: 5px 10px 5px 10px;
  border: 1px solid deepskyblue;
  border-radius: 5px;
  font-size: 15px;
  cursor: pointer;
  transition: all 200ms ease;
}

button:hover {
  border-color: dodgerblue;
}

button:active {
  border-color: blue;
}
</style>
