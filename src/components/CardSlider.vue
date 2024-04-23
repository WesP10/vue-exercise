<template>
  <div id="body">
    <div class="swiper-slide card" v-for="(img, index) in filteredImgs" :key="index">
      <img :src="img.src" :alt="img.alt" />
      <div class="overlay">
        <span>{{ currentSlide }}</span>
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
      currentSlide: 1
    }
  },
  methods: {
    incrSlide (incrAmount) {
      this.currentSlide += incrAmount
      if (this.currentSlide < 1) this.currentSlide = this.imgs.length
      else if (this.currentSlide > this.imgs.length) this.currentSlide = 1
    }
  },
  computed: {
    filteredImgs () {
      return this.imgs
        .map((img, index) => ({ img, index: index + 1 }))
        .filter(({ index }) => {
          return index === this.currentSlide ||
            index === ((this.currentSlide + 1 - 1) % this.imgs.length) + 1 ||
            index === ((this.currentSlide - 1 + this.imgs.length - 1) % this.imgs.length) + 1
        })
        .sort((a, b) => Math.abs(this.currentSlide - a.index) - Math.abs(this.currentSlide - b.index))
        .map(({ img }) => img)
    }
  }
}
</script>

<style scoped>
#body {
  height: 300px;
}
.swiper-slide {
  position: relative;
  width: 500px;
  height: 350px;
  overflow: hidden;
  border-radius: 20px;
  transition: transform 0.5s forwards;
}
.card:nth-child(1) {
  z-index: 1;
}
.card:nth-child(3) {
  transform: scale(0.7) translateY(-272%) translateX(-100%);
  z-index: -1;
}
.card:nth-child(2) {
  transform: scale(0.7) translateY(-130%) translateX(100%);
  z-index: -1;
}
#buttons {
  position: absolute;
  width: 400px;
  top: 480%;
  left: 50vw;
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
