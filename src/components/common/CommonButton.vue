<template lang="pug">
button(:class="{ loader: loader, disabled, pressed }")
  slot(v-if="!loader", name="prefix")
  .loader(v-if="loader")
  p(v-else) {{ text }}
  slot(v-if="!loader", name="suffix")
  slot(v-if="icon", name="icon")
</template>
<script lang="ts" setup>
import { defineProps } from "vue";

const props = defineProps({
  loader: { type: Boolean, default: false },
  disabled: { type: Boolean, default: false },
  pressed: { type: Boolean, default: false },
  text: { type: String },
  icon: { type: Boolean, default: false },
});
</script>
<style lang="scss">
button {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 12px;
  border-radius: 10px;
  height: 42px;

  svg {
    &.suffix {
      margin-left: 5px;
    }

    &.preffix {
      margin-right: 5px;
    }
  }

  p {
    padding: 0;
    margin: 0;
    font-family: var(--font-inter);
    font-size: 14px;
    line-height: 16px;
  }

  .loader {
    border: 4px solid #c4bdbd;
    border-top: 4px solid white;
    border-radius: 50%;
    width: 10px;
    height: 10px;
    animation: spin 1s linear infinite;
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
}

.primary {
  background: #5f14e1;
  border: none;
  color: white;

  &:hover {
    background: #8d6aca;
  }

  &:active {
    background: #3a0a8d;
  }

  &.pressed {
    background: #3a0a8d;
  }

  &.loader {
    background: #c8abff;
  }

  &.disabled {
    background: #c8abff;
  }
}

.secondary {
  background: white;
  border: 1px solid #5f14e1;
  color: #5f14e1;

  &:hover {
    border-color: #8d6aca;
    color: #8d6aca;
  }

  &:active {
    border-color: #8d6aca;
    color: #8d6aca;
  }

  &.pressed {
    border-color: #3a0a8d;
    color: #3a0a8d;
  }

  &.loader {
    background: #f7f7f9;
    border-color: grey;
  }

  &.disabled {
    background: #f7f7f9;
    color: gray;
    border-color: grey;
  }
}

.icon {
  background: white;
  border: 1px solid #5f14e1;
  color: #5f14e1;
  width: fit-content;

  svg {
    &.suffix {
      margin-left: 0;
    }
  }

  &:hover {
    border-color: #8d6aca;
    color: #8d6aca;
  }

  &:active {
    border-color: #8d6aca;
    color: #8d6aca;
  }

  &.pressed {
    border-color: #3a0a8d;
    color: #3a0a8d;
  }

  &.loader {
    background: #f7f7f9;
    border-color: grey;
  }

  &.disabled {
    background: #f7f7f9;
    color: gray;
    border-color: grey;
  }
}

.link {
  background: transparent;
  border: none;
  color: #5f14e1;
  width: fit-content;

  svg {
    &.suffix {
      margin-left: 0;
    }
  }

  &:hover {
    border-color: #8d6aca;
    color: #8d6aca;
  }

  &:active {
    border-color: #8d6aca;
    color: #8d6aca;
  }

  &.pressed {
    border-color: #3a0a8d;
    color: #3a0a8d;
  }

  &.loader {
    background: #f7f7f9;
    border-color: grey;
  }

  &.disabled {
    color: gray;
  }
}
</style>
