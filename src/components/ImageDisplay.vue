<template>
    <div id="body">
      <div id="imgDisplay">
        <div v-for="(img, index) in imgs" :key="index">
          <img :src="img.src" :alt="img.alt">
          <h3 v-text="img.alt"></h3>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'ImageDisplay',
  props: {
    imgs: Array
  }
}
</script>

<style>
#body {
  display: flex;
  justify-content: center;
  align-items: center;
  width: fit-content;
  height: fit-content;
  margin-inline: auto;
}
#imgDisplay {
  padding: 50px;
  display: grid;
  grid-template-columns: repeat(3, 100px);
  grid-template-rows: repeat(3, 100px);
  grid-template-areas:
  "div1 div2 div3"
  "div4 div5 ."
  "div6 div7 div8";
  column-gap: 100px;
}
#imgDisplay > div {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100px;
  height: 100px;
}
#imgDisplay > div > img {
  width: 200px;
  filter: brightness(50%);
  aspect-ratio: 1;
  clip-path: polygon(50% 0, 75% 25%, 100% 50%, 75% 75%, 50% 100%, 25% 75%, 0 50%, 25% 25%);
}
#imgDisplay > div > h3 {
  display: block;
  position: absolute;
  text-align: center;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
#imgDisplay > div:hover > img{
  filter: brightness(100%);
  cursor: pointer;
  animation: imgDisplay 0.5s forwards;
  z-index: 5;
}
#imgDisplay > div:hover > h3 {
  display: none;
}
#imgDisplay > div:nth-child(1) { grid-area: div1; }
#imgDisplay > div:nth-child(2) { grid-area: div2; }
#imgDisplay > div:nth-child(3) { grid-area: div3; }
#imgDisplay > div:nth-child(4) { grid-area: div4; margin-left: 100px;}
#imgDisplay > div:nth-child(5) { grid-area: div5; margin-left: 100px;}
#imgDisplay > div:nth-child(6) { grid-area: div6; }
#imgDisplay > div:nth-child(7) { grid-area: div7; }
#imgDisplay > div:nth-child(8) { grid-area: div8; }
@keyframes imgDisplay {
  50% {
    clip-path: polygon(0 0, 75% 25%, 100% 0, 75% 75%, 100% 100%, 25% 75%, 0 100%, 25% 25%);
  }
  to {
    clip-path: polygon(0 0, 50% 0, 100% 0, 100% 50%, 100% 100%, 50% 100%, 0 100%, 0 50%);
  }
}
</style>
