<script>
import { store } from "../../data/store";

export default {
  data() {
    return {
      store,
      dataOption: "",
    };
  },

  emits: ["change-option"],
};
</script>

<template>
  <div class="container">
    <select v-model="dataOption" @change="$emit('change-option', dataOption)">
      <option value="" selected>Seleziona un archetipo..</option>
      <option
        v-for="(archetype, index) in store.archetypes"
        :key="store.archetypes[index]"
      >
        {{ archetype }}
      </option>
    </select>
  </div>
</template>

<style lang="scss" scoped>
.container {
  width: 80%;
  margin: 0px auto;
  padding: 20px;

  select {
    height: 30px;
    font-size: 20px;
  }
}
</style>
