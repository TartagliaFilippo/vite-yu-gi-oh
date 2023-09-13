<script>
// dipendenze
import axios from "axios";
import { store } from "./data/store";

// componenti
import HeaderApp from "./components/HeaderApp.vue";
import MainApp from "./components/MainApp.vue";

export default {
  data() {
    return {
      urlApi: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
    };
  },

  components: { HeaderApp, MainApp },

  methods: {
    fetchCards() {
      axios.get(this.urlApi).then((response) => {
        const cardsData = response.data.data.map((card) => {
          const { id, card_images, name, archetype } = card;
          return { id, card_images, name, archetype };
        });

        store.cardsList = cardsData;
      });
    },

    fetchArchetype() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/archetypes.php")
        .then((response) => {
          store.archetypes = response.data;
        });
    },
  },

  created() {
    this.fetchCards();

    this.fetchArchetype();
  },
};
</script>

<template>
  <HeaderApp></HeaderApp>
  <MainApp></MainApp>
</template>

<style lang="scss">
@use "./style/general.scss" as *;
</style>
