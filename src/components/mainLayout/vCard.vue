<template>
  <div class="card">
    <div class="container">
      <div class="card__wrapper">
        <div>
          <img :src="image" alt="icon" />
        </div>
        <h2 class="card__name">{{ name }}</h2>
        <MyButton @click.native="$router.push(`/detail/${id}`)">
          Подробнее
        </MyButton>
      </div>
    </div>
  </div>
</template>

<script>
import MyButton from "@/components/UI/MyButton.vue";

export default {
  name: "vCard",
  components: {
    MyButton,
  },
  props: {
    name: {
      type: String,
    },
    image: {
      type: String,
    },
    id: {
      type: Number,
    },
  },
  methods: {
    redirectToDetailPage() {
      this.$router.push({ name: "detail", params: { id: this.id } });
    },
  },
};
</script>

<style lang="scss" scoped>
@use "@/scss/fonts";

.container {
  width: 112px;
  height: 179px;
}
.card {
  border-radius: 4px;
  background: #fff;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.15);
  &__wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  &__name {
    margin-bottom: 22px;
    @include fonts.text-headline-h2;
  }
}
</style>
