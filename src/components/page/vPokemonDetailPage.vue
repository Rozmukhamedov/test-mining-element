<template>
  <header class="detail">
    <div class="container">
      <vCardInfo />
    </div>
  </header>
</template>

<script>
import vCardInfo from "@/components/detailLayout/vCardInfo.vue";

export default {
  name: "vPokemonDetail",
  components: {
    vCardInfo,
  },
};
</script>

<style lang="scss" scoped>
.detail {
  padding: 0 10px;
}
.container {
  max-width: 480px;
  margin: 0 auto;
}
</style>
