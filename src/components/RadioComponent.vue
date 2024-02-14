<template lang="pug">
CommonRadio(v-model="selectedOption", :options="options")
</template>

<script lang="ts" setup>
import CommonRadio from "@/components/common/CommonRadio.vue";
import { ref } from "vue";

const options = ref(["Option 1", "Option 2", "Option 3"]);
const selectedOption = ref("Option 1");
</script>
