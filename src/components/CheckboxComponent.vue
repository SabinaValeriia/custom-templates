<template lang="pug">
div
  CommonCheckbox(
    v-model="selectedOption",
    :options="options",
    @input="selectOptions"
  )
  p Selected options: {{ selectedOption }}
</template>

<script lang="ts" setup>
import CommonCheckbox from "@/components/common/CommonCheckbox.vue";
import { ref } from "vue";

const options = ref(["Option 1", "Option 2", "Option 3"]);
const selectedOption = ref([]);
const selectOptions = (selectedOptions: Array<string>) => {
  selectedOption.value = selectedOptions;
};
</script>

<style lang="scss" scoped>
p {
  font-family: var(--font-inter);
  font-size: 16px;
  line-height: 20px;
}
</style>
