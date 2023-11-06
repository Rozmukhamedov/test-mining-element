<template>
  <div class="pokemon-detail">
    <div class="container">
      <MyButton @click.native="$router.push('/')">Назад</MyButton>
      <div class="pokemon-detail__wrapper">
        <div>
          <img :src="image" alt="icon" class="pokemon-detail__img" />
        </div>
        <div class="pokemon-detail__info">
          <div class="pokemon-detail__block-name">
            <h3 class="pokemon-detail__text-name">name</h3>
            <h2 class="pokemon-detail__name">{{ name }}</h2>
          </div>
          <div class="pokemon-detail__block-stat">
            <div class="pokemon-detail__wrapper-stat">
              <div v-for="(item, index) in stats" :key="index">
                <p class="pokemon-detail__name-stat">
                  {{ item.stat.name }}
                </p>
                <p class="pokemon-detail__count-stat">
                  {{ item.base_stat }}
                </p>
              </div>
            </div>
          </div>
          <div class="pokemon-detail__block-abilities">
            <h3 class="pokemon-detail__abilities-title">abilities</h3>
            <div class="pokemon-detail__abilities-wrapper">
              <p
                v-for="(item, index) in abilities"
                :key="index"
                class="pokemon-detail__card-abilities"
              >
                {{ item }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MyButton from "@/components/UI/MyButton.vue";

export default {
  name: "PokemonDetail",
  components: {
    MyButton,
  },
  data() {
    return {
      name: "",
      image: "",
      abilities: [],
      stats: [],
    };
  },
  methods: {
    async fetchPokemonData(id) {
      try {
        const response = await fetch(
          `https://pokeapi.co/api/v2/pokemon/${id}/`
        );
        const data = await response.json();

        this.name = data.name;
        this.image = data.sprites.front_default;
        this.abilities = data.abilities.map((ability) => ability.ability.name);
        this.stats = data.stats;
      } catch (error) {
        console.error("Ошибка при выполнении запроса:", error);
      }
    },
  },
  async mounted() {
    const pokemonId = this.$route.params.id;
    await this.fetchPokemonData(pokemonId);
  },
};
</script>

<style lang="scss" scoped>
@use "@/scss/fonts";

.container {
  max-width: 480px;
  margin: 0 auto;
}

.pokemon-detail {
  padding: 60px 0;
  &__wrapper {
    margin-top: 35px;
    border-radius: 4px;
    background: #fff;
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.15);
    display: flex;
    gap: 24px;
    align-items: center;
    padding: 24px 16px;
  }
  &__info {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  &__img {
    width: 200px;
  }
  &__block-name {
    display: flex;
    flex-direction: column;
  }
  &__text-name {
    color: #7e7e7e !important;
    @include fonts.text-body-l;
  }
  &__name {
    @include fonts.text-headline-h1;
    text-transform: capitalize;
  }
  &__block-stat {
    width: 250px;
  }
  &__block-abilities {
    display: flex;
    flex-direction: column;
  }
  &__name-stat {
    color: #7e7e7e !important;
    @include fonts.text-body-l;
    margin-bottom: 2px;
  }
  &__count-stat {
    @include fonts.text-headline-h1;
  }
  &__abilities-title {
    color: #7e7e7e !important;
    @include fonts.text-body-l;
  }
  &__wrapper-stat {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 14px;
  }
  &__abilities-wrapper {
    display: flex;
    align-items: center;
  }
  &__card-abilities {
    margin: 2px 8px 0 0;
    padding: 4px 12px;
    color: #fff !important;
    @include fonts.text-body-s;
    border-radius: 4px;
    background: #8d9bcc;
    min-width: 58px;
    min-height: 22px;
    &:last-child {
      margin-right: 0px;
    }
  }
}
@media (max-width: 620px) {
  .pokemon-detail__wrapper {
    display: flex;
    flex-direction: column;
  }
}
</style>
