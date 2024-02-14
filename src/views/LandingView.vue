<template lang="pug">
.landing
  .landing-block
    h1 Custom templates
    .tabs-container
      ul.tabs
        li(
          v-for="(tab, index) in tabs",
          :key="index",
          :class="{ active: activeTabIndex === index }",
          @click="activateTab(index)"
        )
          a(href="#") {{ tab.title }}
  .tab-content
    div(
      v-for="(tab, index) in tabs",
      v-show="activeTabIndex === index",
      :key="index"
    )
      .content(v-if="tab.title === 'Button'")
        h2 Button
        ButtonComponent
      .content(v-else-if="tab.title === 'Input'")
        h2 Input
        InputComponent
        h2 Radio Button
        RadioComponent
        h2 Checkbox
        checkbox-component
        h2 Range Selector
      .content(v-else-if="tab.title === 'Tooltip'")
        tooltips-component
      .content(v-else-if="tab.title === 'Pagination + Calendar'")
        div(v-for="(item, index) in paginatedInventory", :key="index")
          p {{ item.name }}
        CommonPagination(
          :current-page="currentPage",
          :total-pages="totalPages",
          :total-items="items.length",
          :items-per-page="8",
          @changePage="changePage"
        )
        CommonCalendar(:two-date="true")
        CommonCalendar(:one-date="true")
</template>

<script lang="ts" setup>
import ButtonComponent from "@/components/ButtonComponent.vue";
import { computed, ref } from "vue";
import InputComponent from "@/components/InputComponent.vue";
import RadioComponent from "@/components/RadioComponent.vue";
import TooltipsComponent from "@/components/TooltipsComponent.vue";
import CommonPagination from "@/components/common/CommonPagination.vue";
import CommonCalendar from "@/components/common/CommonCalendar.vue";
import CheckboxComponent from "@/components/CheckboxComponent.vue";

const activeTabIndex = ref(0);
const tabs = ref([
  { title: "Button" },
  { title: "Input" },
  { title: "Tooltip" },
  { title: "Pagination + Calendar" },
]);

const items = [
  {
    name: "Test1",
  },
  {
    name: "Test2",
  },
  {
    name: "Test3",
  },
  {
    name: "Test4",
  },
  {
    name: "Test5",
  },
  {
    name: "Test6",
  },
  {
    name: "Test7",
  },
  {
    name: "Test8",
  },
  {
    name: "Test9",
  },
  {
    name: "Test10",
  },
  {
    name: "Test11",
  },
  {
    name: "Test12",
  },
  {
    name: "Test13",
  },
  {
    name: "Test14",
  },
];

const activateTab = (index: number) => {
  activeTabIndex.value = index;
};
const currentPage = ref(1);
const itemsPerPage = ref(8);

const totalPages = computed(() => {
  if (itemsPerPage.value <= 0) {
    return 0;
  }
  return Math.ceil(items.length / itemsPerPage.value);
});

const paginatedInventory = computed(() => {
  const startIndex = (currentPage.value - 1) * itemsPerPage.value;
  const endIndex = Math.min(startIndex + itemsPerPage.value, items.length);
  return items.slice(startIndex, endIndex);
});

function changePage(pageNumber) {
  currentPage.value = pageNumber;
}
</script>

<style lang="scss" scoped>
.landing {
  height: 100vh;

  .tab-content {
    .content {
      padding: 20px 80px;

      div {
        p {
          font-size: 16px;
          line-height: 20px;
          font-family: var(--font-inter);
        }
      }

      h2 {
        font-size: 30px;
        line-height: 40px;
        font-family: var(--font-inter);
        font-weight: bold;
      }
    }
  }

  .landing-block {
    padding: 20px 80px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);

    .tabs-container {
      ul {
        display: flex;
        align-items: center;
        gap: 20px;

        li {
          list-style: none;
          font-size: 20px;
          line-height: 28px;
          font-family: var(--font-inter);
          font-weight: bold;

          a {
            text-decoration: none;
            font-family: var(--font-inter);
            color: black;
            text-wrap: nowrap;
          }
        }
      }
    }
  }

  h1 {
    font-size: 20px;
    line-height: 28px;
    font-family: var(--font-inter);
    font-weight: bold;
    color: black;
    padding: 10px 0;
    margin: 0;
    text-transform: uppercase;
  }
}
</style>
