<template>
    <div id="body">
      <div id="setup">
        <h1>Reaction Time Tester</h1>
        <p>Click the Button that Corresponds to the Image</p>
        <p v-if="answerIndex===1 && !playing">You identified the correct image in {{ score }} ms</p>
        <p v-else-if="answerIndex===2 && !playing">You guessed the wrong photo</p>
        <button @click="start()" :disabled="disabled">Click to Play</button>
      </div>
      <div v-if="playing" id="pic">
          <img :src="imgs[index].src" :alt="imgs[index].alt">
          <div><button v-for="(button, i) in buttons" :key="i" @click="end(button.alt)">{{ button.alt }}</button></div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'ReactionTimer',
  data () {
    return {
      index: 0,
      score: 0,
      timer: null,
      buttons: [this.imgs[0], this.imgs[1], this.imgs[2], this.imgs[3]],
      playing: false,
      disabled: false,
      answerIndex: 0
    }
  },
  methods: {
    randIndex () {
      const startVal = this.index
      while (this.index === startVal) {
        this.index = Math.floor(Math.random() * this.imgs.length)
      }
    },
    createButtons () {
      const indxs = []
      while (indxs.length < 4) {
        const rand = Math.floor(Math.random() * this.imgs.length)
        if (!indxs.includes(rand)) {
          indxs.push(rand)
        }
      }
      indxs[Math.floor(Math.random() * indxs.length)] = this.index
      for (let i = 0; i < indxs.length; i++) {
        this.buttons[i] = this.imgs[indxs[i]]
      }
    },
    start () {
      console.log('Start!')
      this.disabled = true
      this.score = 0
      setTimeout(() => {
        this.playing = true
        this.timer = setInterval(() => {
          this.score += 10
        }, 10)
      }, 1000 + Math.random() * 2000)
    },
    end (alt) {
      if (alt === this.imgs[this.index].alt) {
        this.answerIndex = 1
      } else {
        this.answerIndex = 2
      }
      this.timer = clearInterval(this.timer)
      this.playing = false
      this.randIndex()
      this.createButtons()
      this.disabled = false
    }
  },
  mounted () {
    this.randIndex()
    this.createButtons()
  },
  props: {
    imgs: Array
  }
}
</script>

<style scoped>
#body {
  width: 100%;
}
#body > div {
  width: 90%;
  margin-inline: auto;
}
#setup {
  background: #4b6a89;
  border-radius: 15px;
  padding: 15px;
}
#pic {
  padding: 15px;
  background-color: #d5d4d4;
  border-radius: 10px;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  height: fit-content;
  display: block;
}
#pic img {
  max-height: 250px;
}
#pic > div {
  width: 100%;
  display: flex;
  justify-content: space-around;
}
#pic > div > button {
  background-color: #4b6a89;
  border: none;
  border-radius: 15px;
  color: white;
  padding: 10px 20px;
  text-decoration: none;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  display: inline;
}
#pic > div > button:hover {
  background-color: #2c3e50;
}
button {
  padding: 10px;
}
</style>
