<template>
  <form @submit.prevent="emitForm" class="custom-form">
    <p class="custom-form__title">Введите данные</p>
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

<script setup>
import { reactive } from "vue";

import VButton from "./VButton.vue";
import VInput from "./VInput.vue";

const emit = defineEmits(["onSendForm"]);

const props = defineProps({
  data: Array,
});

const formData = reactive({});

function emitForm() {
  emit("onSendForm", formData);
}
</script>

<style>
.custom-form {
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

.custom-form__title {
  font-size: 23px;
  text-align: center;
  cursor: default;
}
</style>
