<script>
import axios from "axios";
import CardsApp from "./CardsApp.vue";

export default {
  data() {
    return {
      cardsList: [],
    };
  },

  methods: {
    fetchCards() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
        .then((response) => (this.cardsList = response.data.data));
    },
  },

  created() {
    this.fetchCards();
  },

  components: { CardsApp },
};
</script>

<template>
  <div class="container">
    <div class="row">
      <!-- <div class="col" v-for="card in cardsList" :key="card.id">
        <div class="image">
          <img :src="card.card_images[0].image_url" alt="" />
        </div>
        <h4>{{ card.name }}</h4>
        <p>{{ card.archetype }}</p>
      </div> -->
      <CardsApp
        v-for="card in cardsList"
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
