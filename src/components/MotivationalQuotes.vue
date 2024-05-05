<template>
    <div id="body">
      <h1>Motivational Quotes by {{ name }}</h1>
      <img :src="imgs[index].src" :alt="imgs[index].alt">
      <p>{{ quotes[index] }}</p>
      <button @click="randIndex()">Click for Next Quote</button>
    </div>
</template>

<script>
export default {
  name: 'MotivationalQuotes',
  data () {
    return {
      index: 0,
      quotes: [
        'Believe you can, and you’re halfway there.',
        'The only limit to our realization of tomorrow will be our doubts of today.',
        'Success is not final, failure is not fatal: It is the courage to continue that counts.',
        'Your time is limited, don’t waste it living someone else’s life.',
        'The future belongs to those who believe in the beauty of their dreams.',
        'Hardships often prepare ordinary people for an extraordinary destiny.',
        'Don’t watch the clock; do what it does. Keep going.',
        'You are never too old to set another goal or to dream a new dream.'
      ]
    }
  },
  methods: {
    randIndex () {
      const startVal = this.index
      while (this.index === startVal) {
        this.index = Math.floor(Math.random() * this.quotes.length)
      }
    }
  },
  mounted () {
    this.randIndex()
  },
  props: {
    name: String,
    imgs: Array
  }
}
</script>

<style scoped>
    #body {
      padding: 30px;
      display: block;
      width: calc(100% - 60px);
    }
    #body img {
      margin-top: 20px;
      max-height: 250px;
      padding: 15px;
      background-color: #d5d4d4;
      border-radius: 10px;
      box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
      margin-inline: auto;
    }
    #body p {
      padding: 30px;
      clear: both;
      display: block;
    }
    #body > button {
      background-color: #4b6a89;
      border: none;
      border-radius: 15px;
      color: white;
      padding: 15px 32px;
      text-decoration: none;
      font-size: 16px;
      margin: 4px auto;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #2c3e50;
    }
    #body > * {
      display: block;
      color: black;
    }
</style>
