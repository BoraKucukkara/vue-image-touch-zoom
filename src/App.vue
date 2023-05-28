<template>
  <header>Vue Image Zoom</header>
  <div class="feed" v-for="image in images" :key="image.src">
    <div class="feed-header">
      <img src="https://avatars.githubusercontent.com/u/89361281?v=4" alt="Bora Kucukkara"> John Doe
    </div>

    <img-touch-zoom :img="image"/>

    <div class="feed-footer">
      <i class="fa-regular fa-heart"></i>
      <b>9128 Likes</b>
    </div>
    <p>{{image.alt}}</p>
    <small>3 hours ago</small>
  </div>
  <footer>
    <small>vue-image-touch-zoom by Bora Kucukkara</small>
    <div class="copyright">
      <a href="https://github.com/BoraKucukkara/vue-check-out" title="Bora Kucukkara / vue-check-out on Github">
        <svg height="24" aria-hidden="true" viewBox="0 0 16 16" version="1.1" width="24" data-view-component="true" class="octicon octicon-mark-github v-align-middle">
          <path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"></path>
        </svg>
      </a>
      <a href="https://www.borakucukkara.com/" title="Bora Kucukkara personal web site">
        <img src="https://www.borakucukkara.com/borakucukkara.png" width="24">
      </a>
    </div>
  </footer>

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
  margin:0 auto;
  padding:0;
  color: #666;
  box-sizing: border-box;
  touch-action: pan-x pan-y;
}
#app {
  font-family: sans-serif;
}
header {
  height: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #efefef;
  margin-bottom: 1rem;
  font-weight: bold;
}
.feed {
  width: 100%;
  margin-bottom:2rem
}
.feed-header {
  display: flex;
  padding: .5rem;
  align-items: center;
  font-weight: bold;
}
.feed-header > img {
  width: 2.5rem;
  border-radius: 50%;
  border:2px solid coral;
  margin-right: .5rem;
}
.feed-footer {
  display: flex;
  align-items: center;
  padding: .5rem;
}
i {
  color:#ccc;
  padding-right: .5rem;
  font-size:2rem;
}
p {
  padding: 0 1rem;
  margin:0;
}
small {
  padding: 0 1rem;
}
footer {
  height: 3rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #eaeaea;
}
.copyright a {padding:.3rem; opacity: .7; transition: all .3s;}
.copyright a:hover {opacity: 1}
</style>
