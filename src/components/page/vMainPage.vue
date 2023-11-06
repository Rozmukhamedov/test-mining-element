<template>
  <div class="main">
    <div class="container">
      <vCardItems />
    </div>
  </div>
</template>

<script>
import vCardItems from "@/components/mainLayout/vCardItems.vue";

export default {
  name: "MainLayout",
  components: {
    vCardItems,
  },
};
</script>

<style lang="scss" scoped>
.main {
  padding: 0 10px;
}
.container {
  max-width: 620px;
  margin: 0 auto;
}
</style>
