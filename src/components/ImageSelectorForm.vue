<template>
  <div id="body">
    <div id="form">
      <div id="selector"> Select Photo:
        <div v-for="(img, i) in imgs" :key="i" class="option" @click="changeImage(i)">
          {{ img.alt }}
        </div>
      </div>
      <img :src="imgs[index].src" :alt="imgs[index].alt" id="img">
    </div>
  </div>
</template>

<script>
export default {
  name: 'ImageSelectorForm',
  props: {
    imgs: Array
  },
  data () {
    return {
      index: 0
    }
  },
  methods: {
    changeImage (i) {
      this.index = i
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Freeman&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Freeman", sans-serif;
  font-weight: 400;
  font-style: normal;
}
#body {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
#form {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 60%;
  height: 35vw;
  text-align: center;
  background: linear-gradient(25deg, rgba(255, 255, 255, 0.9) 0%, rgba(255, 255, 255, 0.7) 50%, rgba(255, 255, 255, 0.5) 100%);
  border-radius: 10px;
  box-shadow: 8px 14px 8px rgba(0, 0, 0, 0.4);
  border: 3px solid black;
  margin-inline: auto;
}
#selector {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  width: 100%;
  height: 100%;
  color: black;
}
.option {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 60%;
  color: black;
  padding-block: 3px;
  cursor: pointer;
  position: relative;
}
.option:after {
  content:'';
  position:absolute;
  bottom:0;
  left:0;
  right:0;
  background: rgba(0, 0, 0, 0.3);
  height: 3px;
  border-radius: 10px;
}
.option::before {
  content:'';
  position:absolute;
  top:0;
  left:0;
  right:0;
  background: rgba(0, 0, 0, 0.3);
  height: 3px;
  border-radius: 10px;
}
#img {
  aspect-ratio: 16/12;
  height: 35vw;
  object-fit: cover;
  display: block;
  justify-content: center;
  align-items: center;
  border: 3px solid black;
  border-radius: 0 10px 10px 0;
}
@media screen and (max-width: 1200px){
  #form {
    width: 90%;
    height: 50vw;
  }
  #img {
    height: 50vw;
  }
}
</style>
