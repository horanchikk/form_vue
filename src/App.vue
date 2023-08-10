<template>
  <VForm @onSendForm="send" :data="formElements" />
</template>

<script setup lang="ts">
import VForm from "./components/VForm.vue";
import { TFormElement } from "./types/form";

const formElements: TFormElement[] = [
  {
    name: "lastname",
    placeholder: "Фамилия",
    type: "text",
  },
  {
    name: "firstname",
    placeholder: "Имя",
    type: "text",
  },
  {
    name: "surname",
    placeholder: "Отчество",
    type: "text",
  },
  {
    name: "birthday",
    placeholder: "Дата рождения",
    type: "date",
  },
  {
    name: "agree",
    placeholder: "Согласен с обработкой данных",
    type: "checkbox",
  },
];

function send(e: object) {
  alert(JSON.stringify({ ...e }));
}
</script>
