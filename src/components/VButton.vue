<template>
  <button class="custom-button">
    <slot />
  </button>
</template>

<style>
.custom-button {
  color: black;
  padding: 5px 10px 5px 10px;
  border: 1px solid deepskyblue;
  border-radius: 5px;
  font-size: 15px;
  cursor: pointer;
  transition: all 200ms ease;
}

.custom-button:hover {
  border-color: dodgerblue;
}

.custom-button:active {
  border-color: blue;
}
</style>
