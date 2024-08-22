<template>
  <div id="body">
    <div v-for="(img, index) in displayedCards" :key="img.alt" class="swiper-slide card">
      <img :src="img.src" :alt="img.alt" :key="img.src"/>
      <div class="overlay">
        <span>{{ indexs[index]}}</span>
        <h2>{{ img.alt }}</h2>
      </div>
    </div>
    <div id="buttons">
      <button @click="incrSlide(-1)">Previous</button>
      <button @click="incrSlide(1)">Next</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CardSlider',
  props: {
    imgs: Array
  },
  data () {
    return {
      currentSlide: 0,
      prev: this.imgs.length - 1,
      next: 1,
      indexs: [],
      displayedCards: []
    }
  },
  mounted () {
    this.displayedCards = [this.imgs[this.currentSlide], this.imgs[this.prev], this.imgs[this.next]]
    this.indexs = [this.currentSlide + 1, this.prev + 1, this.next + 1]
  },
  methods: {
    incrSlide (incrAmount) {
      this.currentSlide += incrAmount
      if (this.currentSlide < 0) this.currentSlide = this.imgs.length - 1
      else if (this.currentSlide > this.imgs.length - 1) this.currentSlide = 0
      this.prev = this.currentSlide - 1
      if (this.prev < 0) this.prev = this.imgs.length - 1
      else if (this.prev > this.imgs.length - 1) this.prev = 0
      this.next = this.currentSlide + 1
      if (this.next < 0) this.next = this.imgs.length - 1
      else if (this.next > this.imgs.length - 1) this.next = 0

      this.indexs = [this.currentSlide + 1, this.prev + 1, this.next + 1]
      this.displayedCards = [this.imgs[this.currentSlide], this.imgs[this.prev], this.imgs[this.next]]
    }
  }
}
</script>

<style scoped>
#body {
  height: 300px;
  position: relative;
  margin-bottom: 200px;
}
.swiper-slide {
  position: relative;
  width: 500px;
  height: 350px;
  overflow: hidden;
  border-radius: 20px;
}
.card:nth-child(1) {
  z-index: 1;
  animation: slide1 0.5s forwards;
}
@keyframes slide1 {
  0% {
    transform: scale(1) translateY(0%) translateX(-100%);
  }
  100% {
    transform: scale(1) translateY(0) translateX(0);
  }
}
.card:nth-child(3) {
  z-index: -1;
  animation: slide2 0.5s forwards;
}
@keyframes slide2 {
  0% {
    transform: scale(0.1) translateY(-272%) translateX(-100%);
  }
  100% {
    transform: scale(0.7) translateY(-272%) translateX(-100%);
  }
}
.card:nth-child(2) {
  z-index: -1;
  animation: slide3 0.5s forwards;
}
@keyframes slide3 {
  0% {
    transform: scale(0.7) translateY(-130%) translateX(0);
  }
  100% {
    transform: scale(0.7) translateY(-130%) translateX(100%);
  }
}
#buttons {
  position: absolute;
  width: 400px;
  top: 120%;
  left: 50%;
  transform: translateX(-50%);
}
#buttons > button {
  position: relative;
  background-color: #4b6a89;
  border: none;
  border-radius: 15px;
  color: white;
  padding: 15px 32px;
  text-decoration: none;
  font-size: 16px;
  margin: 4px 20px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
#buttons > button:hover {
  background-color: #2c3e50;
}
.overlay {
  position: absolute;
  color: #fff;
  inset: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to top, #0f2027, transparent);
  background-repeat: no-repeat;
  background-size: cover;
}

.overlay span {
  position: absolute;
  top: 0;
  right: 0;
  padding: 7px 18px;
  margin: 10px;
  border-radius: 20px;
  letter-spacing: 2px;
  font-size: 0.8rem;
  font-weight: 700;
  font-family: inherit;
  background: rgba(133, 133, 133, 0.095);
  box-shadow: inset 2px -2px 20px rgba(59, 59, 59, 0.2),
    inset -3px 3px 3px rgba(255, 255, 255, 0.4);
  backdrop-filter: blur(74px);
}
.overlay h2 {
  position: absolute;
  bottom: 0;
  left: 0;
  color: #fff;
  font-weight: 400;
  font-size: 1.1rem;
  line-height: 1.4;
  margin: 0 0 20px 20px;
}
</style>
