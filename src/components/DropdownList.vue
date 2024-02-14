<template lang="pug">
.checkbox-block(
  v-if="(type === 'checkbox' && membersData) || (type === 'checkbox' && membersData)"
)
  p {{ title }}
  div
    button(
      v-if="checkedItem.length !== filteredData.length",
      @click.prevent="selectAll"
    ) Select All
    button(@click.prevent="clearAll") Clear
ul(
  v-if="filteredData.length",
  :class="[type === 'checkbox' ? 'checkbox' : '', type, className]"
)
  li(
    v-for="(item, index) in filteredData",
    :key="index",
    :class="item.status",
    @click.stop="selectItem(item)"
  )
    .image-item(v-if="type === 'lead'")
      img.logo(v-if="item.logo", :src="JSON.parse(item.logo.name)", alt="name")
      //img.logo(v-else, :src="require(`@/assets/icons/gender.svg`)")
    .image-item(v-if="type === 'menu'")
      i.icon(:class="[item.icon, item.class]")
    button.checkbox(
      v-if="type === 'checkbox' && !checkedItem",
      @click.prevent="toggleSelect(item)"
    )
      i.check.icon
    button.checkbox(
      v-else-if="type === 'checkbox' && checkedItem",
      :class="{ active: checkedItem.includes(item) }",
      @click.prevent="toggleSelect(item)"
    )
      i.check.icon
    button.checkbox(
      v-else-if="type === 'checkbox' && allItems",
      :class="{ active: allItems.includes(item) }",
      @click.prevent="toggleSelect(item)"
    )
      i.check.icon
    p {{ item.name }}
ul.not-founds(v-else)
  li
    i.icon.user
    p Not results
</template>

<script lang="ts" setup>
// import { filterFunction } from "@/composables/projectsAction";
import { defineProps, ref } from "vue";

const props = defineProps({
  type: { type: String },
  title: { type: String },
  className: { type: String },
  checkedItem: { type: Array },
  filteredData: { type: Array },
  membersData: { type: String, default: "false" },
});
const emit = defineEmits(["selectedItem", "clear", "allItem"]);
const selectedItems = ref(props.checkedItem);
console.log(selectedItems);
const isActive = ref(false);
// const { selected } = filterFunction([]);
const selectItem = (item: { name: string; id: number }) => {
  emit("selectedItem", item);
};

const selectAll = () => {
  const allItems = [...props.filteredData];
  for (const item of allItems) {
    emit("allItem", item);
  }
};

const clearAll = () => {
  emit("clear");
};
</script>
