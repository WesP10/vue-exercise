<template>
    <div id="body">
        <ImageDisplay :imgs="imgs"/>
        <ReactionTimer :imgs="imgs"/>
        <MotivationalQuotes name="Weston"/>
        <BrickGallery :imgs="imgs"/>
        <CardSlider :imgs="imgs"/>
  </div>
</template>

<script>
import MotivationalQuotes from '../components/MotivationalQuotes.vue'
import ImageDisplay from '../components/ImageDisplay.vue'
import ReactionTimer from '../components/ReactionTimer.vue'
import BrickGallery from '../components/BrickGallery.vue'
import CardSlider from '../components/CardSlider.vue'

export default {
  name: 'App',
  data () {
    return {
      imgs: [
        {
          src: require('../assets/BabyWall.jpg'),
          alt: 'Baby Wall'
        },
        {
          src: require('../assets/BrownShoe.jpg'),
          alt: 'Brown Shoe'
        },
        {
          src: require('../assets/ChickenCoops.jpg'),
          alt: 'Chicken Coops'
        },
        {
          src: require('../assets/FunnySleding.jpg'),
          alt: 'Funny Sleding'
        },
        {
          src: require('../assets/GreenGirl.jpg'),
          alt: 'GreenGirl'
        },
        {
          src: require('../assets/Iguana.jpg'),
          alt: 'Iguana'
        },
        {
          src: require('../assets/ScreamingApple.jpg'),
          alt: 'Screaming Apple'
        },
        {
          src: require('../assets/Tower.jpg'),
          alt: 'Tower'
        }
      ]
    }
  },
  components: {
    MotivationalQuotes,
    ImageDisplay,
    ReactionTimer,
    BrickGallery,
    CardSlider
  }
}
</script>

<style scoped>
#body {
  margin-top: 14dvh;
  display: block;
  text-align: center;
  height: calc(100vh - 12vh);
}
</style>
