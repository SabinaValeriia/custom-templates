<template lang="pug">
.button
  .row
    .col
      h3
      h3 Primary
      h3 Secondary
      h3 Primary + ICON
      h3 Secondary + ICON
      h3 Links
      h3 ICON ONLY
    .col
      h3 Default
      CommonButton.primary(:text="'Button name'")
      CommonButton.secondary(:text="'Button name'")
      CommonButton.primary(:text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.secondary(:text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.link(:text="'Button name'")
      CommonButton.icon(:icon="true")
        template(#icon)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
    .col
      h3 Hover
      CommonButton.primary(:text="'Button name'")
      CommonButton.secondary(:text="'Button name'")
      CommonButton.primary(:text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.secondary(:text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.link(:text="'Button name'")
      CommonButton.icon(:icon="true")
        template(#icon)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
    .col
      h3 Pressed
      CommonButton.primary(:pressed="true", :text="'Button name'")
      CommonButton.secondary(:pressed="true", :text="'Button name'")
      CommonButton.primary(:pressed="true", :text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.secondary(:pressed="true", :text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.link(:pressed="true", :text="'Button name'")
      CommonButton.icon(:icon="true")
        template(#icon)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
    .col
      h3 Loading
      CommonButton.primary(:loader="true", :text="'Button name'")
      CommonButton.secondary(:loader="true", :text="'Button name'")
      CommonButton.primary(:loader="true", :text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.secondary(:loader="true", :text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="#5F14E1",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.link(:text="'Button name'")
      CommonButton.icon(:loader="true", :icon="true")
    .col
      h3 Disabled
      CommonButton.primary(:disabled="true", :text="'Button name'")
      CommonButton.secondary(:disabled="true", :text="'Button name'")
      CommonButton.primary(:disabled="true", :text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="white",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.secondary(:disabled="true", :text="'Button name'")
        template(#suffix)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="grey",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="grey",
              stroke-width="2",
              stroke-linecap="round"
            )
      CommonButton.link(:disabled="true", :text="'Button name'")
      CommonButton.icon(:disabled="true", icon="true")
        template(#icon)
          svg.suffix(
            width="20",
            height="20",
            viewBox="0 0 20 20",
            fill="white",
            xmlns="http://www.w3.org/2000/svg"
          )
            path(
              d="M3.33337 9.06241L3.33337 14.5C3.33337 16.1568 4.67654 17.5 6.33341 17.5L11.7709 17.4999M8.33337 2.4999L13.9584 2.4999C14.9939 2.4999 15.8334 3.33937 15.8334 4.3749L15.8334 12.4999C15.8334 13.5354 14.9939 14.3749 13.9584 14.3749L8.33337 14.3749C7.29784 14.3749 6.45838 13.5354 6.45837 12.4999L6.45837 4.3749C6.45837 3.33937 7.29784 2.4999 8.33337 2.4999Z",
              stroke="grey",
              stroke-width="2",
              stroke-linecap="round"
            )
</template>

<script lang="ts" setup>
import CommonButton from "@/components/common/CommonButton.vue";
</script>
<style lang="scss">
.button {
  width: 100%;

  .row {
    display: flex;
    align-items: flex-end;
    gap: 20px;

    .col {
      display: flex;
      flex-direction: column;
      gap: 20px;

      h3 {
        padding: 12px;
        margin: 0;
        font-size: 16px;
        font-family: var(--font-inter);
        text-align: center;
      }
    }
  }
}
</style>
