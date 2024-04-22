<template>
  <div id="body">
    <img v-for="(img, i) in imgs" :key="i" :src="img.src" :alt="img.alt">
    <img v-for="(img, i) in imgs" :key="i" :src="img.src" :alt="img.alt" class="duplicate">
  </div>
</template>

<script>
export default {
  name: 'BrickGallery',
  props: {
    imgs: Array
  }
}
</script>

<style scoped>
#body{
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  overflow: hidden;
  mask: linear-gradient(90deg, transparent, black 15% 85%, transparent);
}
#body img {
  width: 25%;
  height: 50%;
  object-fit: cover;
  filter: contrast(80%) brightness(80%);
}
#body img:nth-child(-n+4) {
  animation: slide 30s infinite linear;
}
#body img:nth-child(n+5):nth-child(-n+8) {
  animation: slide 30s infinite reverse linear;
}
#body img:nth-child(n+9):nth-child(-n+12) {
  animation: slide2 30s infinite linear;
}
#body img:nth-child(n+13):nth-child(-n+16) {
  animation: slide2 30s infinite reverse linear;
}
@keyframes slide {
  0% {
    transform: translateX(0) translateY(0);
  }
  100% {
    transform: translateX(400%) translateY(0);
  }
}
@keyframes slide2 {
  0% {
    transform: translateX(-400%) translateY(calc(-200% - 8px));
  }
  100% {
    transform: translateX(0%) translateY(calc(-200% - 8px));
  }
}
</style>
