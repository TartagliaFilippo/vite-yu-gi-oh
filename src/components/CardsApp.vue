<script>
export default {
  props: {
    image_url: String,
    name: String,
    archetype: String,
  },
};
</script>

<template>
  <div class="col">
    <div class="image">
      <img :src="image_url" alt="" />
    </div>
    <h4>{{ name }}</h4>
    <p>{{ archetype }}</p>
  </div>
</template>

<style lang="scss" scoped>
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
</style>
