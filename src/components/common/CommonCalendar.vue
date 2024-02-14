<template lang="pug">
div
  .form-group(v-if="oneDate")
    label.label-inter Select date
    input(
      v-model="selectedDate",
      :placeholder="`${selectedDate}`",
      type="text",
      @click="isOpen = !isOpen"
    )

  .form-groups(v-if="twoDate")
    .form-group
      label.label-inter Start
      input(
        v-model="selectedStartDate",
        :placeholder="`${startDate}`",
        type="text",
        @click="isOpen = !isOpen"
      )
    .form-group
      label.label-inter End
      input(
        v-model="selectedEndDate",
        :placeholder="`${endDate}`",
        type="text",
        @click="isOpen = !isOpen"
      )

  .calendar(v-if="isOpen")
    .header
      h2 {{ formattedCurrentMonth }}
      .block
        button.prev(@click="prevMonth")
          i.icons.arrow
        button.next(@click="nextMonth")
          i.icons.arrow
    table
      thead
        tr
          th.day(v-for="day in daysOfWeek", :key="day") {{ day }}
      tbody
        tr(v-for="week in weeks", :key="week")
          td(
            v-for="day in week",
            :key="day.date",
            :class="{ today: isToday(day.date), 'before-current-day': isBeforeCurrentDay(day.date), next: isNextMonth(day.date, currentMonth), range: isDateInRange(day.date), border: isStartDate(day.date), last: isEndDate(day.date) }",
            @click="selectDate(day.date)"
          )
            div(
              :class="{ start: isStartDate(day.date), end: isEndDate(day.date) }"
            ) {{ formatDate(day.date) }}
</template>

<script lang="ts" setup>
import { computed, defineProps, ref } from "vue";
import dayjs from "dayjs";

const isOpen = ref(false);
const currentMonth = ref(dayjs());
const selectedDate = ref("Placeholder");
const selectedStartDate = ref(null);
const selectedEndDate = ref(null);
const startDate = ref("XX/XX/XXXX");
const endDate = ref("XX/XX/XXXX");

const props = defineProps({
  oneDate: Boolean,
  twoDate: Boolean,
});

const isStartDate = (date) => {
  if (props.twoDate) {
    return date.isSame(startDate.value);
  } else {
    return false;
  }
};

const isEndDate = (date) => {
  if (props.twoDate) {
    return date.isSame(endDate.value);
  } else {
    return false;
  }
};

const isDateInRange = (date) => {
  if (props.twoDate && startDate.value && endDate.value) {
    return (
      date.isSame(startDate.value) ||
      date.isSame(endDate.value) ||
      (date.isAfter(startDate.value) && date.isBefore(endDate.value))
    );
  } else {
    return false;
  }
};

const daysOfWeek = computed(() => ["вс", "пн", "вт", "ср", "чт", "пт", "сб"]);

const formattedCurrentMonth = computed(() =>
  currentMonth.value.format("MMMM YYYY")
);

const formatDate = (date: object) => (date ? date.format("D") : "");

const isToday = (date: object) => date && date.isSame(dayjs(), "day");

const isBeforeCurrentDay = (date: object) => date.isBefore(dayjs(), "day");

const isNextMonth = (date: object, currentMonth: string) => {
  const nextMonth = currentMonth.add(1, "month");
  return date.isSame(nextMonth, "month");
};

const prevMonth = () => {
  currentMonth.value = currentMonth.value.subtract(1, "month");
};

const nextMonth = () => {
  currentMonth.value = currentMonth.value.add(1, "month");
};

const selectDate = (date: object) => {
  const formattedDate = date.format("DD.MM.YYYY");

  if (props.twoDate) {
    if (!startDate.value) {
      startDate.value = date;
      selectedStartDate.value = formattedDate;
    } else if (!endDate.value && date.isAfter(startDate.value)) {
      endDate.value = date;
      selectedEndDate.value = formattedDate;
    } else {
      startDate.value = date;
      endDate.value = null;
      selectedStartDate.value = formattedDate;
      selectedEndDate.value = null;
    }
  } else {
    startDate.value = date;
    selectedStartDate.value = formattedDate;
  }

  selectedDate.value = formattedDate;
  isOpen.value = false;
};

const weeks = computed(() => {
  const firstDayOfMonth = currentMonth.value.startOf("month");
  const startOfMonth = firstDayOfMonth.day();
  const daysInMonth = firstDayOfMonth.daysInMonth();

  const previousMonth = currentMonth.value.subtract(1, "month");

  const nextMonth = currentMonth.value.add(1, "month");
  const weeks = [];
  let currentWeek = [];

  Array.from({ length: startOfMonth }, (_, i) => {
    currentWeek.push({ date: previousMonth.date(i + 1) });
  });
  Array.from({ length: daysInMonth }, (_, i) => {
    currentWeek.push({ date: firstDayOfMonth.date(i + 1) });

    if (currentWeek.length === 7) {
      weeks.push(currentWeek);
      currentWeek = [];
    }
  });
  Array.from({ length: 7 - currentWeek.length }, (_, i) => {
    currentWeek.push({ date: nextMonth.date(i + 1) });
  });

  weeks.push(currentWeek);

  return weeks;
});
</script>

<style lang="scss" scoped>
.form-groups {
  display: flex;

  .form-group {
    padding: 20px 0 0 0;
    margin-right: 12px;

    input {
      width: 120px;
    }
  }
}

.form-group {
  padding: 20px 0;
  display: flex;
  flex-direction: column;

  span {
    display: none;
  }

  label {
    margin-bottom: 8px;
    font-family: var(--font-inter);
    font-size: 16px;
    line-height: 20px;
    font-weight: bold;
  }

  input {
    cursor: pointer;
    position: relative;
    width: 100%;
    height: 22px;
    padding: 14px 16px 14px 16px;
    border-radius: 8px;
    border: 1px solid #ecebeb;
    gap: 8px;
    outline: none;
    color: #3d3734;
    font-family: var(--font-inter);
    font-size: 16px;
    font-weight: 400;
    line-height: 24px;
    letter-spacing: 0em;
    text-align: left;

    &::after {
      content: "";
      display: block;
      width: 16px;
      height: 16px;
      position: absolute;
      right: 16px;
      top: 14px;
      pointer-events: none;
    }

    &::placeholder {
      font-family: var(--font-inter);
      font-size: 16px;
      font-weight: 400;
      line-height: 24px;
      letter-spacing: 0em;
      text-align: left;
    }

    &:hover {
      border-color: #3a0a8d;
    }

    &:active {
      border-color: #3a0a8d;
    }
  }
}

.calendar {
  width: fit-content;
  min-height: 312px;
  border-radius: 12px;
  background: #fff;
  box-shadow: 0px 0px 2px 0px rgba(5, 9, 26, 0.12),
    0px 4px 8px 0px rgba(5, 9, 26, 0.08), 0px 4px 16px 0px rgba(5, 9, 26, 0.05);
  padding: 8px;
  margin: 10px 0 0 10px;

  table {
    border-spacing: 0;
  }

  h2 {
    color: #3d3734;
    text-align: center;
    font-family: var(--font-inter);
    font-size: 16px;
    font-style: normal;
    font-weight: 500;
    line-height: 24px;
    text-wrap: nowrap;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 8px 8px 0;
  }

  .block {
    display: flex;
    justify-content: flex-end;
    align-items: center;

    button {
      border: none;
      border-radius: 16px;
      background: #3a0a8d;
      display: flex;
      width: 32px;
      height: 32px;
      padding-left: 0px;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;

      i {
        width: 16px;
        height: 16px;
        left: 8px;
      }

      &.prev {
        transform: rotate(90deg);
      }

      &.next {
        transform: rotate(270deg);
        margin-left: 16px;
      }
    }
  }

  th,
  td {
    text-align: center;
    font-family: var(--font-inter);
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
    padding: 10px;
    position: relative;
    cursor: pointer;

    &.today {
      color: #3a0a8d;
    }

    &.before-current-day {
      color: #b1afae;
      cursor: not-allowed;
      pointer-events: none;
      cursor: not-allowed;
    }

    &.next {
      color: #b1afae;
    }

    &.range {
      background-color: #cfcbd5;
    }

    &.border {
      border-radius: 16px 0 0 16px;
    }

    &.last {
      border-radius: 0 16px 16px 0;
    }
  }

  th.day {
    color: #b1afae;
  }

  .start {
    color: white;
    border-radius: 21px;
    background: #3a0a8d;
    width: 37px;
    height: 40px;
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .end {
    color: white;
    border-radius: 21px;
    background: #3a0a8d;
    width: 37px;
    height: 40px;
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
