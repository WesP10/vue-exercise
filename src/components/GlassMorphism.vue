<template>
  <div id="body">
    <div id="container">
      <div v-for="(img, index) in imgs" :key="index" class="glass" id="card" :style="{animationDelay: delays[index] + 's' }">
        <img :src="img.src" :alt="img.alt"/>
        <h1>{{ img.alt }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GlassMorphism',
  data () {
    return {
      delays: [1.25, 0.625, 2.5, 1.875, 3.125, 0, 3.75, 4.375]
    }
  },
  props: {
    imgs: Array
  }
}
</script>

<style scoped>
#body {
  width: 100%;
  height: fit-content;
  overflow-x: hidden;
}
#container {
  display: flex;
  width: calc(100% - 40px);
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding: 10px;
}
.glass {
  background: rgba(255, 255, 255, 0.2);
  border-radius: 10px;
  padding: 20px;
  backdrop-filter: blur(5px);
  border: 1px solid rgba(255, 255, 255, 0.18);
}
#card {
  position: relative;
  width: 18vw;
  height: 12vw;
  margin: 10px;
  box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.7);
  animation: bounce 15s infinite;
}
@keyframes bounce {
  0%, 50%, 80%, 100% {
    transform: translateY(0) translateX(0);
  }
  30% {
    transform: translateY(-20px) translateX(10px);
  }
  70% {
    transform: translateY(-10px) translateX(-10px);
  }
  90% {
    transform: translateY(-5px) translateX(-5px);
  }
}
div.glass h1 {
  color: transparent;
  font-size: 2em;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
div.glass img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 10px;
}
#card:hover img{
  filter: brightness(0.3);
}
#card:hover h1{
  color: white;
}
</style>
