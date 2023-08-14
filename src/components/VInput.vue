<template>
  <div class="custom-input">
    <input
      class="custom-input__element"
      @input="send"
      v-model="data"
      :type="props.type"
      :placeholder="props.placeholder"
      :id="props.id"
      v-if="props.type !== 'checkbox'"
      :class="{ 'custom-input__isEmpty': isEmpty }"
      required
    />
    <input
      class="custom-input__element custom-input__checkbox"
      @change="send"
      v-model="data"
      :type="props.type"
      :placeholder="props.placeholder"
      :id="props.id"
      v-else
      required
    />
    <label
      class="custom-input__label"
      :for="props.id"
      v-if="props.type === 'checkbox' || props.type === 'date'"
      >{{ props.placeholder }}</label
    >
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  type: String,
  placeholder: String,
  id: String,
});

const emit = defineEmits(["update:modelValue"]);
const isEmpty = ref(true);
const data = ref();

function send() {
  isEmpty.value = !data.value;
  emit("update:modelValue", data.value);
}
</script>

<style>
.custom-input {
  display: flex;
  gap: 5px;
}

.custom-input__element {
  width: 100%;
  border: 1px solid rgba(0, 150, 0, 0.5);
  padding: 10px;
  outline: none;
  border-radius: 3px;

  transition: all 200ms ease;
}

.custom-input__element:focus {
  font-size: 15px;
}

.custom-input__checkbox {
  width: 15px;
  height: 15px;
}

.custom-input__isEmpty {
  border: 1px solid rgba(255, 0, 0, 0.5);
}
</style>
