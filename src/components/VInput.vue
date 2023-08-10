<template>
  <div>
    <input
      @input="send"
      :type="props.type"
      :placeholder="props.placeholder"
      :id="props.id"
      v-if="props.type !== 'checkbox'"
      :class="{ isEmpty: isEmpty }"
      required
    />
    <input
      @change="send"
      :type="props.type"
      :placeholder="props.placeholder"
      :id="props.id"
      v-else
      required
    />
    <label
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

function send(e) {
  isEmpty.value = !e.target.value;
  emit("update:modelValue", e.target.value);
}
</script>

<style scoped lang="scss">
input {
  width: 100%;
  border: 1px solid rgba(0, 150, 0, 0.5);
  padding: 10px;
  outline: none;
  border-radius: 3px;

  transition: all 200ms ease;

  &[type="checkbox"] {
    width: 15px;
    height: 15px;
  }

  &:focus {
    font-size: 15px;
  }
}

.isEmpty {
  border: 1px solid rgba(255, 0, 0, 0.5);
}

div {
  display: flex;
  gap: 5px;
}
</style>
