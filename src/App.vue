<template>
  <VForm @onSendForm="send" :data="formElements" />
</template>

<script setup>
import VForm from "./components/VForm.vue";

const formElements = [
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

function send(e) {
  alert(JSON.stringify({ ...e }));
}
</script>
