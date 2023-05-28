<template>
  <img-touch-zoom v-for="image in images" :img="image" :key="image.src"/>
</template>

<script>
import imgTouchZoom from "@/components/img-touch-zoom.vue"
export default {
  name: 'App',
  data() {
    return {
      images: [
        {src:"001.jpg",alt:"The Eastern Veil Nebula in the constellation of Cygnus. Photo by Scott Lord on Unsplash"},
        {src:"002.jpg",alt:"Apollo 11 astronaut Buzz Aldrin walks on the surface of the moon on July 20, 1969, in a photograph taken by Neil Armstrong. Photo by History in HD on Unsplash"},
        {src:"003.jpg",alt:"The Pelican nebula. Photo by Aldebaran S on Unsplash"},
        {src:"004.jpg",alt:"Sirenum Fossae, Mars"},
        {src:"005.jpg",alt:"Photo by NASA on Unsplash"},
      ]
    }
  },
  components: {
    imgTouchZoom
  }
}
</script>

<style>
body {
  margin:0;
  padding:0;
  width: 100vw;
  height: 100dvh;
  overflow-y: scroll;
  overflow-x: hidden;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
