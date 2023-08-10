<template>
  <form @submit.prevent="emitForm">
    <h2>Введите данные</h2>
    <VInput
      v-for="el in props.data"
      :type="el.type"
      :placeholder="el.placeholder"
      :id="el.name"
      v-model="formData[el.name]"
    />
    <VButton type="submit">Отправить</VButton>
  </form>
</template>

<script setup lang="ts">
import { reactive } from "vue";

import VButton from "./VButton.vue";
import VInput from "./VInput.vue";
import { TFormElement } from "../types/form";

const emit = defineEmits(["onSendForm"]);

const props = defineProps({
  data: Array<TFormElement>,
});

const formData = reactive({});

function emitForm() {
  emit("onSendForm", formData);
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 30px;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.3);
  box-shadow: 0 10px 20px -3px rgba(0, 0, 0, 0.3);
  font-family: sans-serif;
  font-size: 15px;
}

h2 {
  text-align: center;
  cursor: default;
}
</style>
