<template>
    <img :src="require('@/assets/images/' + img.src)"
         :alt="img.alt"
         ref="img"
         @touchstart="start"
         @touchmove="move"
         @touchend="reset"/>
  <div class="img-desc" v-if="desc">{{img.alt}}</div>
</template>
<script>
export default {
  data() {
    return {
      firstX:0,
      firstY:0,
      newX: 0,
      newY: 0,
      dist1: 0,
      dist2: 0,
      imgOffsetY: 0,
      desc:false // img alt tag content comes with props
    }
  },
  props: {
    img: Object
  },
  methods: {
    start(event) {
      this.$refs.img.style.zIndex = "99"
      this.firstX = Math.floor(event.touches[0].pageX)
      this.firstY = Math.floor(event.touches[0].pageY) - this.imgOffsetY
      this.imgOffsetY = this.$refs.img.offsetTop
      if (event.targetTouches.length === 2) {
        this.dist1 = Math.hypot(
            event.touches[0].pageX - event.touches[1].pageX,
            event.touches[0].pageY - event.touches[1].pageY);
        this.$refs.img.style.transformOrigin = this.firstX + "px " + this.firstY+ "px"
      }
    },
    move(event) {
      this.$refs.img.style.zIndex = "99"
      if (event.targetTouches.length === 2 && event.changedTouches.length === 2) {
        this.dist2 = Math.hypot(
            event.touches[0].pageX - event.touches[1].pageX,
            event.touches[0].pageY - event.touches[1].pageY);
        if (this.dist1 > this.dist2) {
          this.$refs.img.style.scale = "1"
        }
        // view alt tag in zoom mode
        if (this.$refs.img.style.scale > 1) {this.desc = true}

        if (this.dist1 < this.dist2) {
          this.newX = Math.floor(event.touches[0].pageX)
          this.newY = Math.floor(event.touches[0].pageY - this.imgOffsetY)
          this.$refs.img.style.scale = (this.dist2 / this.dist1).toFixed(1)
          // scale limit
          if (this.$refs.img.style.scale > 3) {
            this.$refs.img.style.scale = "3"
          }
          this.$refs.img.style.transform = "translate(" + (this.newX - this.firstX) + "px," + (this.newY - this.firstY) / 2 + "px)"
        }
      }
    },
    reset() {
      this.desc = false
      this.$refs.img.style.zIndex = "0"
      this.$refs.img.style.scale = "1"
      this.$refs.img.style.transform = "translate(0,0)"
    }
  }
}

</script>
<style scoped>
img {
  width: 100vw;
  transition: all .2s linear; /* required for scale anim */
  position: relative; /* required for z-index */
}
.img-desc { /* optional - view alt tag in zoom condition  */
  position: fixed;
  height: auto;
  width: calc(100vw - 2rem);
  bottom:0;
  padding: 1rem;
  color:#fff;
  background: #00000077;
  z-index: 100;
  backdrop-filter: blur(5px);
  animation: fade-in .5s ease forwards;
}
@keyframes fade-in {from {opacity: 0} to {opacity: 1}}
</style>