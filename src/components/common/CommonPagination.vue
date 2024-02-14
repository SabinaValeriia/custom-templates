<template lang="pug">
.pagination
  nav(aria-label="Pagination")
    p(v-if="totalItems > 0") {{ displayRange }}
    ul
      li(v-if="currentPage > 1", @click="changePage(currentPage - 1)")
        img.prev(src="@/assets/Vector.svg")
      li(
        v-for="pageNumber in totalPages",
        :key="pageNumber",
        :class="{ current: pageNumber === currentPage }",
        @click="changePage(pageNumber)"
      ) {{ pageNumber }}
      li(v-if="currentPage < totalPages", @click="changePage(currentPage + 1)")
        img.next(src="@/assets/Vector.svg")
</template>

<script setup>
import { computed, defineEmits, defineProps } from "vue";

const props = defineProps({
  currentPage: Number,
  totalPages: Number,
  totalItems: Number,
  itemsPerPage: Number,
});
const emit = defineEmits(["changePage"]);

const startIndex = computed(
  () => (props.currentPage - 1) * props.itemsPerPage + 1
);
const endIndex = computed(() =>
  Math.min(startIndex.value + props.itemsPerPage - 1, props.totalItems)
);

const displayRange = computed(() => {
  if (props.totalItems === 0) return "0 of 0";
  return `${startIndex.value}-${endIndex.value} of ${props.totalItems}`;
});

function changePage(pageNumber) {
  emit("changePage", pageNumber);
}
</script>

<style lang="scss" scoped>
.pagination {
  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;

    p {
      font-size: 16px;
      line-height: 20px;
      font-family: var(--font-inter);
      color: black;
    }
  }

  ul {
    display: flex;
    gap: 10px;

    li {
      list-style: none;
      padding: 10px 15px;
      cursor: pointer;

      &:hover {
        background: #a58fd5;
        border-radius: 22px;
        color: white;
      }

      &.current {
        background: #3a0a8d;
        color: white;
        border-radius: 22px;
      }

      a {
        text-decoration: none;
        font-size: 16px;
        line-height: 20px;
        font-family: var(--font-inter);
        color: black;
      }

      img {
        &.next {
          transform: rotate(268deg);
        }

        &.prev {
          transform: rotate(90deg);
        }
      }
    }
  }
}
</style>
