<template lang="pug">
common-input(
  :class="getValidationClass($v, 'title')",
  :type="'text'",
  :value-input="form.title",
  :is-error="getValidationClass($v, 'title')",
  @set-data="form.title = $event"
)
  template(v-if="$v.title.required.$invalid", #errors)
    span This field is required.
common-input.disabled(
  :class="getValidationClass($v, 'key')",
  :type="'text'",
  :value-input="form.key",
  :is-error="getValidationClass($v, 'key')",
  @set-data="form.key = $event"
)
  template(v-if="$v.key.required.$invalid", #errors)
    span This field is required.
common-input.error(
  :class="getValidationClass($v, 'description')",
  :type="'description'",
  :value-input="form.description",
  :is-error="getValidationClass($v, 'description')",
  @set-data="form.description = $event"
)
  template(v-if="$v.description.required.$invalid", #errors)
    span This field is required.
common-input(
  :class="getValidationClass($v, 'lead')",
  :type="'text'",
  :value-input="form.lead",
  :is-error="getValidationClass($v, 'lead')",
  @set-data="form.lead = $event"
)
  template(#suffix)
    svg(
      width="16",
      height="16",
      viewBox="0 0 16 16",
      fill="none",
      xmlns="http://www.w3.org/2000/svg"
    )
      path(
        d="M8.00251 14.9297L0 1.07422H6.14651L8.00251 4.27503L9.84583 1.07422H16L8.00251 14.9297Z",
        fill="black"
      )
  template(v-if="$v.lead.required.$invalid", #errors)
    span This field is required.
</template>

<script lang="ts" setup>
import CommonInput from "@/components/common/CommonInput.vue";
import { getValidationClass } from "@/types/authValidation";
import { computed, ref } from "vue";
import useVuelidate from "@vuelidate/core";
import { required } from "@vuelidate/validators";

const defaultState = {
  title: "",
  key: "",
  description: "",
  lead: "",
  image: "",
  members: [],
  tags: [],
};

const form = ref({
  ...defaultState,
});

const rules = computed(() => {
  const rules: any = {
    title: { required },
    key: { required },
    description: { required },
    lead: { required },
    image: {
      required,
    },
    members: { required },
  };
  return rules;
});

const $v = useVuelidate(rules, form);
</script>

<style lang="scss"></style>
