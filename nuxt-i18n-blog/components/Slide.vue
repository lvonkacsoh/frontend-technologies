<template>
  <div class="slide" v-editable="blok">
    <img :src="blok.image" />
  </div>
</template>

<script>
export default {
  props: ["blok"]
};
</script>

<style lang="scss">
.slide {
  width: 100%;

  img {
    width: 10%;
    position: relative;
    left: 45%;
  }
}
</style>