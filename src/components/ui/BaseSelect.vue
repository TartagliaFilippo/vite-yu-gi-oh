<script>
import { store } from "../../data/store";

export default {
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="container">
    <select name="archetypes" id="archetypes">
      <option v-for="archetype in store.archetypes">
        {{ archetype.archetype_name }}
      </option>
    </select>
  </div>
</template>

<style lang="scss" scoped></style>
