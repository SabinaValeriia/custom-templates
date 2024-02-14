<template lang="pug">
.custom-select
  .option(v-for="(option, index) in options", :key="index")
    input.checkbox-input(
      :id="'option_' + index",
      :value="option",
      :checked="selectedOptions.includes(option)",
      type="checkbox",
      @change="handleChange(option)"
    )
    label.checkbox-label(:for="'option_' + index")
      .checkbox.checked(v-if="selectedOptions.includes(option)")
        span &#10003;
      .checkbox.unchecked(v-else)
      | {{ option }}
  p Selected options: {{ selectedOptions }}
</template>

<script lang="ts" setup>
import { defineEmits, defineProps, ref } from "vue";

const props = defineProps({
  options: {
    type: Array,
    required: true,
  },
  value: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["input"]);

const selectedOptions = ref(props.value || []);

const handleChange = (option: string) => {
  if (selectedOptions.value.includes(option)) {
    selectedOptions.value = selectedOptions.value.filter(
      (item) => item !== option
    );
  } else {
    selectedOptions.value.push(option);
  }
  emit("input", selectedOptions.value);
};
</script>

<style scoped>
.custom-select {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;

  p {
    font-family: var(--font-inter);
    font-size: 14px;
    line-height: 16px;
  }

  .option {
    margin-bottom: 5px;

    label {
      display: flex;
      align-items: center;
      gap: 10px;
    }
  }

  .checkbox-label {
    cursor: pointer;
    font-family: var(--font-inter);
    font-size: 14px;
    line-height: 16px;
  }

  .checkbox-input {
    display: none;
  }

  .checked {
    background: #3a0a8d;

    span {
      color: white;
    }
  }

  .unchecked {
    background: white;
    border: 1px solid grey;
    border-radius: 5px;
  }

  .checkbox {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 22px;
    height: 22px;
    border-radius: 5px;
  }
}
</style>
