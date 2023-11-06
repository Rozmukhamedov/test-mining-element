<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "MyButton",
};
</script>

<style lang="scss" scoped>
@use "@/scss/fonts";

.btn {
  width: 96px;
  height: 24px;
  border-radius: 4px;
  background: #b5dbdd;
  @include fonts.text-button-s;
  text-transform: lowercase;
}
</style>
