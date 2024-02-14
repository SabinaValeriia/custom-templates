<template lang="pug">
.main
  .content
    h3 Tooltip
    common-tooltip
      template(#action) Up, Left
      template(#content)
        .tooltip.up-left-block.up-left Up, Left
    common-tooltip
      template(#action) Up, Center
      template(#content)
        .tooltip.up-center-block.up-center Up, Center
    common-tooltip
      template(#action) Up, Right
      template(#content)
        .tooltip.up-right.up-right-block Up, Right
    common-tooltip
      template(#action) Center, Right
      template(#content)
        .tooltip.center-right.center-right-block Center, Right
    common-tooltip
      template(#action) Center, Left
      template(#content)
        .tooltip.center-left.center-left-block Center, Left
    common-tooltip
      template(#action) Down, Left
      template(#content)
        .tooltip.down-left.down-left-block Down, Left
    common-tooltip
      template(#action) Down, Center
      template(#content)
        .tooltip.down-center.down-center-block Down, Center
    common-tooltip
      template(#action) Down, Right
      template(#content)
        .tooltip.down-right.down-right-block Down, Right
</template>

<script lang="ts" setup>
import CommonTooltip from "@/components/common/CommonTooltip.vue";
</script>
<style lang="scss">
.main {
  display: flex;
  flex-wrap: wrap;

  h3 {
    font-family: var(--font-inter);
    font-size: 2em;
    margin: 0.67em 0;
  }
}

.block {
  width: 70%;
  height: 100%;
  overflow-y: auto;

  p {
    margin: 80px 20px;
    cursor: pointer;
    font-family: "Inter", sans-serif;
    font-weight: 400;
  }

  .content {
    height: 200vh;
  }
}

.up-left-block {
  position: absolute;
  transform: translate3d(100px, 276px, 0px);
  top: 0px;
  left: 0px;
}

.up-center-block {
  position: absolute;
  transform: translate3d(61px, 374px, 0px);
  top: 0px;
  left: 0px;
}

.up-right-block {
  position: absolute;
  transform: translate3d(11px, 470px, 0px);
  top: 0px;
  left: 0px;
}

.center-right-block {
  position: absolute;
  transform: translate3d(-69px, 529px, 0px);
  top: 0px;
  left: 0px;
}

.center-left-block {
  position: absolute;
  transform: translate3d(190px, 625px, 0px);
  top: 0px;
  left: 0px;
}

.down-left-block {
  position: absolute;
  transform: translate3d(97px, 683px, 0px);
  top: 0px;
  left: 0px;
}

.down-center-block {
  position: absolute;
  transform: translate3d(63px, 780px, 0px);
  top: 0px;
  left: 0px;
}

.down-right-block {
  position: absolute;
  transform: translate3d(23px, 874px, 0px);
  top: 0px;
  left: 0px;
}

.up-left::before {
  top: -7px;
  left: 16px;
}

.up-center::before {
  top: -7px;
  left: 50%;
  transform: translateX(-50%);
}

.up-right::before {
  top: -7px;
  left: calc(100% - 20px);
}

.center-right::before {
  transform: rotate(90deg);
  top: 40%;
  left: calc(100%);
}

.center-left::before {
  top: 40%;
  left: calc(-3%);
  transform: rotate(270deg);
}

.down-left::before {
  top: 98%;
  transform: rotate(180deg);
  left: 10%;
}

.down-center::before {
  top: 98%;
  left: 50%;
  transform: rotate(180deg);
}

.down-right::before {
  top: 98%;
  left: 90%;
  transform: rotate(180deg);
}
</style>
