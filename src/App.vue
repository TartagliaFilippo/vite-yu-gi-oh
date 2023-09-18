<script>
// dipendenze
import axios from "axios";
import { store } from "./data/store";

// componenti
import HeaderApp from "./components/HeaderApp.vue";
import MainApp from "./components/MainApp.vue";
import BaseSelect from "./components/ui/BaseSelect.vue";

export default {
  data() {
    return {
      urlApiGeneral: "https://db.ygoprodeck.com/api/v7/cardinfo.php",
      urlApi: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
    };
  },

  components: { HeaderApp, MainApp, BaseSelect },

  methods: {
    fetchCards(urlApi) {
      axios.get(urlApi).then((response) => {
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
          store.archetypes = response.data.map((archetype) => {
            return archetype.archetype_name;
          });
        });
    },

    handleOptions(dataOption) {
      const endpoint = `${this.urlApiGeneral}?archetype=${dataOption}`;
      this.fetchCards(endpoint);
    },
  },

  created() {
    this.fetchCards(this.urlApi);
    this.fetchArchetype();
  },
};
</script>

<template>
  <HeaderApp></HeaderApp>
  <BaseSelect @change-option="handleOptions"></BaseSelect>
  <MainApp></MainApp>
</template>

<style lang="scss">
@use "./style/general.scss" as *;
</style>
