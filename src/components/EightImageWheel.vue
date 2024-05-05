<template>
  <div id="body">
    <div id="wheel">
      <div v-for="(img, index) in imgs" :key="index" class="image">
        <img :src="img.src" :alt="img.alt">
        <img :src="img.src" :alt="img.alt"/>
        <h1>{{ img.alt }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'EightImageWheel',
  props: {
    imgs: Array
  }
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
}
#body {
  width: 800px;
  height: 800px;
  position: relative;
}
#wheel {
  display: flex;
  width: 800px;
  height: 800px;
  justify-content: center;
  align-items: center;
  border: 5px white solid;
  background: rgba(255, 255, 255, 0.3);
  border-radius: 50%;
}
.image {
  position: absolute;
  width: 250px;
  aspect-ratio: 1;
  transform-origin: 50% 147.5%;
  transform: translateY(-250px) rotate(0deg);
  animation: spin 16s infinite;
  cursor: pointer;
  filter: brightness(0.3);
  transition: filter 0.5s;
}
img {
  width: 100%;
  height: 100%;
  top: 0;
  left: 0%;
  object-fit: cover;
}
.image img:nth-child(1) {
  position: absolute;
  transform: rotate(180deg);
  filter: blur(15px);
}
.image img:nth-child(2) {
  transition: clip-path 0.5s;
  clip-path: polygon(20% 15%, 80% 15%, 100% 100%, 80% 90%, 60% 80%, 40% 80%, 20% 90%, 0 100%);
}
.image h1 {
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  color: white;
  font-size: 2rem;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 0.5rem;
  opacity: 0;
  transition: top 0.5s, opacity 0.5s;
}
.image:hover {
  filter: brightness(1);
  z-index: 1;
}
.image:hover img:nth-child(2) {
  clip-path: polygon(50% 0, 100% 0, 100% 50%, 100% 100%, 50% 100%, 0 100%, 0 50%, 0 0);
}
.image:hover h1 {
  top: 130%;
  opacity: 1;
}
.image:nth-child(1) {
  animation-delay: 0s;
}
.image:nth-child(2) {
  animation-delay: -2s;
}
.image:nth-child(3) {
  animation-delay: -4s;
}
.image:nth-child(4) {
  animation-delay: -6s;
}
.image:nth-child(5) {
  animation-delay: -8s;
}
.image:nth-child(6) {
  animation-delay: -10s;
}
.image:nth-child(7) {
  animation-delay: -12s;
}
.image:nth-child(8) {
  animation-delay: -14s;
}
@keyframes spin {
  0% {
    transform: translateY(-250px) rotate(0deg);
  }
  12.5% {
    transform: translateY(-250px) rotate(45deg);
  }
  25% {
    transform: translateY(-250px) rotate(90deg);
  }
  37.5% {
    transform: translateY(-250px) rotate(135deg);
  }
  50% {
    transform: translateY(-250px) rotate(180deg);
  }
  62.5% {
    transform: translateY(-250px) rotate(225deg);
  }
  75% {
    transform: translateY(-250px) rotate(270deg);
  }
  87.5% {
    transform: translateY(-250px) rotate(315deg);
  }
  100% {
    transform: translateY(-250px) rotate(360deg);
  }
}
</style>
