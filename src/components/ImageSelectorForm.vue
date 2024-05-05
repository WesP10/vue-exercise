<template>
  <div id="body">
    <div id="form">
      <div id="selector"> Select Photo:
        <div v-for="(img, index) in imgs" :key="index">
          {{ img.alt }}
        </div>
        <img :src="imgs[0].src" :alt="imgs[0].alt">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ImageSelectorForm',
  props: {
    imgs: Array
  }
}
</script>

<style scoped>

</style>
