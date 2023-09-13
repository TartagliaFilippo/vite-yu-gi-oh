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
    .col {
      width: 19%;
      height: 210px;

      .image {
        width: 100%;
        height: 150px;

        img {
          width: 100%;
          max-height: 100%;
        }
      }

      h4 {
        font-size: 10px;
        text-align: center;
      }

      p {
        font-size: 8px;
        text-align: center;
      }
    }
  }
}
</style>
