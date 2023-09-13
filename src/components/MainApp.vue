<script>
import ListCards from "./ListCards.vue";

export default {
  components: { ListCards },
};
</script>

<template>
  <div class="wrapper">
    <ListCards></ListCards>
  </div>
</template>

<style lang="scss" scoped>
.wrapper {
  background-color: orange;
  padding-top: 50px;
}
</style>
