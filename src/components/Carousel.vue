<script>
export default {
  name: "Carousel",

  data: () => ({
    carouselItems: [...new Array(5)],
    model: {
      buttonView: false,
    },
    currentSlide: 1,
    dots__active: "",
  }),

  methods: {
    showButtons() {
      this.model.buttonView = true;
    },
    removeButtons() {
      this.model.buttonView = false;
    },
    nextSlide() {
      if (this.currentSlide < this.carouselItems.length) {
        this.currentSlide++;
      } else if (this.currentSlide === this.carouselItems.length) {
        this.currentSlide = 1;
      }
    },
    prevSlide() {
      if (this.currentSlide !== 1) {
        this.currentSlide--;
      } else if (this.currentSlide === 1) {
        this.currentSlide = this.carouselItems.length;
      }
    },
    changeSlide(index) {
      this.currentSlide = index + 1;
    },
  },
}
</script>

<template>
  <div>
    <div
        class="carousel"
        @mouseleave="removeButtons()"
        @mouseover="showButtons()"
    >
      <div
          v-for="(_, index) of carouselItems"
          :key="index"
          :class="{ 'display-none': index !== currentSlide }"
          style="position: absolute;">
      </div>
      <button v-if="model.buttonView" class="prev" @click="prevSlide()">prev</button>
      <h2>
        Slide {{ currentSlide }}
      </h2>
      <button v-if="model.buttonView" class="next" @click="nextSlide()">next</button>
      <div class="dots__block">
        <button
            v-for="(dots, index)  of carouselItems"
            :key="dots"
            :class="{ 'dots__active': index + 1 === currentSlide }"
            class="dots"
            @click="changeSlide(index)">
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>

.display-none {
  display: none;
}

.carousel {
  background-color: green;
  width: 100%;
  height: 300px;
  text-align: center;
  position: relative;
}

.prev, .next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}

.prev {
  left: 10px;
}

.next {
  right: 10px;
}

.dots {
  background-color: transparent;
  border: 1px solid #fff;
  border-radius: 50%;
  width: 10px;
  height: 13px;
  cursor: pointer;
  margin: 0 5px;
}

.dots__block {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
}

.dots:hover {
  background-color: black;
}

.dots__active {
  background-color: black;
}

h2 {
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 300px;
}
</style>