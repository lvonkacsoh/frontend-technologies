<template>
  <div v-editable="blok" class="teaser">
    <component v-if="slide" :blok="slide" :is="slide.component"></component>
    <div class="teaser__pag">
      <button
        @click="handleDotClick(index)"
        class="teaser__pag-dot"
        v-for="(blok, index) in blok.body"
        :key="index"
        :class="{'teaser__pag-dot--current': index === currentSlide}"
      >Next</button>
    </div>
  </div>
</template>


<script>
export default {
  props: ["blok"],
  data() {
    return {
      currentSlide: 0
    };
  },
  computed: {
    slide() {
      return (
        this.blok.body.find((slide, index) => this.currentSlide === index) ||
        null
      );
    }
  },
  methods: {
    handleDotClick(index) {
      this.currentSlide = index;
    }
  }
};
</script>

<style lang="scss">
.teaser__pag {
  width: 100%;
  text-align: center;
  margin: 30px 0;
}

.teaser__pag-dot {
  text-indent: -9999px;
  border: 0;
  border-radius: 50%;
  width: 17px;
  height: 17px;
  padding: 0;
  margin: 5px 6px;
  background-color: #ccc;
  -webkit-appearance: none;
  cursor: pointer;

  &--current {
    background-color: #000;
  }
}
</style>
