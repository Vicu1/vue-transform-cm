<script>
export default {
  name: "Carousel",

  data: () => ({
    carouselItems: [...new Array(5)],
    model: {
      buttonView: false,
    },
    currentSlide: 0
  }),

  methods: {
    buttons() {
      this.model.buttonView = true;
    },
    removeButtons() {
      this.model.buttonView = false;
    },
    nextSlide(){
      if (this.currentSlide < this.carouselItems.length){
      this.currentSlide++;
      }else if (this.currentSlide === this.carouselItems.length){
        this.currentSlide = 0;
      }
    },
    prevSlide(){
      if (this.currentSlide !== 0){
        this.currentSlide--;
      }else if (this.currentSlide === 0){
        this.currentSlide = this.carouselItems.length;
      }
    }
  }
}
</script>

<template>
  <div>
    <div class="carousel"
        @mouseleave="removeButtons()"
        @mouseover="buttons()">
      <div :class="{ 'display-none': index !== currentSlide }" v-for="(slide, index) of carouselItems" :key="index"
           style="position:absolute;"></div>
      <button @click="prevSlide()" v-if="model.buttonView" class="prev">prev</button>
      <h2>
        Slide {{ currentSlide }}
      </h2>
      <button @click="nextSlide()" v-if="model.buttonView" class="next">next</button>
      <div class="dots__block">
        <button class="dots" v-for="dot of carouselItems" :key="dot">

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
  height: 10px;
  cursor: pointer;
  margin: 0 5px;
}
.dots__block{
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
}
.dots:hover{
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