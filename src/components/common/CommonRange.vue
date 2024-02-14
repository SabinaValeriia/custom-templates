<template>
  <div id="app">
    <input
      v-model="value"
      max="100"
      min="0"
      type="range"
      @input="updateSlider"
    />
    <div :style="{ backgroundSize }" class="range-background"></div>
    <output>{{ value }}</output>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";

const value = ref(20);
const backgroundSize = ref("20% 100%");

const updateSlider = (e: Event) => {
  const clickedElement = e.target as HTMLInputElement;
  const min = parseFloat(clickedElement.min);
  const max = parseFloat(clickedElement.max);
  const val = parseFloat(clickedElement.value);

  backgroundSize.value = `${((val - min) * 100) / (max - min)}% 100%`;
};
</script>

<style scoped>
body {
  font-family: "Roboto", sans-serif;
  background-color: #000;
  color: #add8e6;
}

#app {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 50%;
  transform: translate(-50%, -50%);
}

.data {
  text-align: center;
  margin-top: 24px;
}

/* Slider CSS */
input[type="range"] {
  -webkit-appearance: none;
  display: block;
  width: 100%;
  margin: 16px 0;
  background: #3e3e3f;
  background-image: -webkit-gradient(
    linear,
    20% 0%,
    20% 100%,
    color-stop(0%, #add8e6),
    color-stop(100%, #add8e6)
  );
  background-image: -webkit-linear-gradient(left, #add8e6 0%, #add8e6 100%);
  background-image: -moz-linear-gradient(left, #add8e6 0%, #add8e6 100%);
  background-image: -o-linear-gradient(to right, #add8e6 0%, #add8e6 100%);
  background-image: linear-gradient(to right, #add8e6 0%, #add8e6 100%);
  background-repeat: no-repeat;
}

input[type="range"]:focus {
  outline: none;
}

input[type="range"]::-webkit-slider-runnable-track {
  width: 100%;
  height: 4px;
  cursor: pointer;
  box-shadow: none;
  background: transparent;
  border-radius: 0px;
  border: none;
}

input[type="range"]::-webkit-slider-thumb {
  box-shadow: none;
  border: 4px solid #add8e6;
  height: 16px;
  width: 16px;
  border-radius: 2px;
  background: #3e3e3f;
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: -6px;
}

input[type="range"]:focus::-webkit-slider-runnable-track {
  background: transparent;
}

input[type="range"]::-moz-range-track {
  width: 100%;
  height: 4px;
  cursor: pointer;
  box-shadow: none;
  background: transparent;
  border-radius: 0px;
  border: none;
}

input[type="range"]::-moz-range-thumb {
  box-shadow: none;
  border: 4px solid #add8e6;
  height: 16px;
  width: 16px;
  border-radius: 2px;
  background: #ffffff;
  cursor: pointer;
}

input[type="range"]::-ms-track {
  width: 100%;
  height: 4px;
  cursor: pointer;
  background: transparent;
  border-color: transparent;
  color: transparent;
}

input[type="range"]::-ms-fill-lower {
  background: transparent;
  border: none;
  border-radius: 0px;
  box-shadow: none;
}

input[type="range"]::-ms-fill-upper {
  background: transparent;
  border: none;
  border-radius: 0px;
  box-shadow: none;
}

input[type="range"]::-ms-thumb {
  box-shadow: none;
  border: 4px solid #add8e6;
  height: 16px;
  width: 16px;
  border-radius: 2px;
  background: #ffffff;
  cursor: pointer;
  height: 4px;
}

input[type="range"]:focus::-ms-fill-lower {
  background: transparent;
}

input[type="range"]:focus::-ms-fill-upper {
  background: transparent;
}

/* End Range Slider */
</style>
