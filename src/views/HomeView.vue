<template>
    <div id="body">
        <ImageDisplay :imgs="imgs"/>
        <ReactionTimer :imgs="imgs"/>
        <MotivationalQuotes name="Weston" :imgs="imgs"/>
        <BrickGallery :imgs="imgs"/>
        <CardSlider :imgs="imgs"/>
        <GlassMorphism :imgs="imgs"/>
        <EightImageWheel :imgs="imgs"/>
        <ImageSelectorForm :imgs="imgs"/>
  </div>
</template>

<script>
import MotivationalQuotes from '@/components/MotivationalQuotes.vue'
import ImageDisplay from '@/components/ImageDisplay.vue'
import ReactionTimer from '@/components/ReactionTimer.vue'
import BrickGallery from '@/components/BrickGallery.vue'
import CardSlider from '@/components/CardSlider.vue'
import GlassMorphism from '@/components/GlassMorphism.vue'
import EightImageWheel from '@/components/EightImageWheel.vue'
import ImageSelectorForm from '@/components/ImageSelectorForm.vue'

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
          alt: 'Green Girl'
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
    CardSlider,
    GlassMorphism,
    EightImageWheel,
    ImageSelectorForm
  }
}
</script>

<style scoped>
#body {
  margin-top: 14dvh;
  display: block;
  text-align: center;
}
</style>
