<template>
  <div class="home">
    <vPokemonDetail />
  </div>
</template>

<script>
import vPokemonDetail from "@/components/page/vPokemonDetailPage.vue";

export default {
  name: "HomeView",
  components: {
    vPokemonDetail,
  },
};
</script>
