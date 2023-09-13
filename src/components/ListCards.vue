<script>
import CardsApp from "./CardsApp.vue";
import { store } from "../data/store";

export default {
  data() {
    return {
      store,
    };
  },

  components: { CardsApp },
};
</script>

<template>
  <div class="container">
    <div class="row">
      <CardsApp
        v-for="card in store.cardsList"
        :key="card.id"
        :image_url="card.card_images[0].image_url"
        :name="card.name"
        :archetype="card.archetype"
      ></CardsApp>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  width: 80%;
  margin: 0 auto;

  .row {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
}
</style>
