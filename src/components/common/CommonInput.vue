<template lang="pug">
.form-group(:class="type")
  .label-group
    label {{ capitalizeFirstLetter(`${type}`) }}
  .form-item(v-if="open")
    slot(name="prefix")
    input(
      v-model="inputVal",
      :type="type",
      :placeholder="capitalizeFirstLetter(`${type}`)",
      :class="{ withIcon }",
      @focus="isFocused = true"
    )
    slot(name="suffix")
  slot(name="errors")
</template>

<script lang="ts" setup>
import { computed, defineEmits, defineProps, ref, watch } from "vue";

const props = defineProps({
  type: { type: String },
  valueInput: {
    type: String,
  },
  isError: { type: Boolean },
  withIcon: { type: Boolean, default: false },
});

const emit = defineEmits(["setData"]);

const open = ref(true);

const inputVal = computed({
  get() {
    return props.valueInput;
  },
  set(val) {
    emit("setData", val);
  },
});

const capitalizeFirstLetter = (word: string) => {
  return word.charAt(0).toUpperCase() + word.slice(1);
};
const toggleInput = () => {
  // event.stopPropagation();
  open.value = !open.value;
};
watch(
  () => props.isError.error,
  (newError) => {
    if (newError) {
      open.value = true;
    }
  }
);
</script>

<style lang="scss">
.form-group {
  &.disabled {
    .form-item {
      input {
        background: #f7f7f9;
        border: 1px solid #9ca1ad;
        pointer-events: none;
      }
    }
  }

  &.error {
    .label-group {
      color: red;
    }

    span {
      display: block;
      color: red;
      margin-top: 5px;
    }

    .form-item {
      input {
        background: #f7f7f9;
        border: 1px solid red;
        pointer-events: none;
      }
    }
  }

  span {
    display: none;
    font-family: var(--font-inter);
    font-size: 14px;
    line-height: 16px;
  }

  .form-item {
    width: fit-content;
    position: relative;
    display: flex;
    align-items: center;

    svg {
      position: absolute;
      right: 10px;
    }

    input {
      border: 1px solid #3a0a8d;
      border-radius: 5px;
      background: white;
      padding: 10px;
      font-family: var(--font-inter);
      font-size: 14px;
      line-height: 16px;

      &::placeholder {
        color: grey;
      }

      &:focus {
        outline: 2px solid #000000;
      }
    }
  }

  .label-group {
    margin: 10px 0;

    label {
      font-family: var(--font-inter);
      font-size: 16px;
      line-height: 20px;
      font-weight: bold;
    }
  }
}
</style>
