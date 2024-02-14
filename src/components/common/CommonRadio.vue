<template lang="pug">
.custom-select
  .option(v-for="(option, index) in options", :key="index")
    input.radio-input(
      :id="option",
      v-model="selectedOption",
      :value="option",
      type="radio",
      @change="handleChange"
    )
    label.radio-label(:for="option") {{ option }}
  p Selected option: {{ selectedOption }}
</template>

<script lang="ts" setup>
import { defineEmits, defineProps, ref } from "vue";

const props = defineProps({
  options: {
    type: Array,
    required: true,
  },
  value: {
    type: String,
    required: true,
  },
});

const emit = defineEmits(["input"]);

const selectedOption = ref(props.value);

const handleChange = () => {
  emit("input", selectedOption.value);
};
</script>

<style scoped>
.custom-select {
  font-family: var(--font-inter);
  font-size: 14px;
  line-height: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;

  p {
    font-family: var(--font-inter);
    font-size: 16px;
    line-height: 20px;
  }

  .option {
    margin-bottom: 5px;
    display: flex;
    align-items: center;
  }

  .radio-label {
    cursor: pointer;
  }

  .radio-input {
    margin-right: 5px;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    width: 16px;
    height: 16px;
    border: 2px solid #666;
    border-radius: 50%;
    outline: none;
    cursor: pointer;

    &:checked {
      background-color: #3a0a8d;
    }
  }
}
</style>
