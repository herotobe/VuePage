<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" @contextmenu="handlePrevent" />
  <canvas ref="canvas"></canvas>
  <HelloWorld msg="Hello Vue 3 + Vite" />
</template>
<script>
import img from './assets/logo.png';
export default {
  mounted(){
    const canvas = this.$refs.canvas
    this.imageToCanvas(img, canvas)
  },
 methods:{
   handlePrevent(e) {
     e.preventDefault();
   },
  async imageToCanvas(url, canvas) {
    return new Promise((resolve, reject) => {
    const img = new Image()

    img.src = url
    const c = canvas.getContext('2d')
    img.onload = function () {
    canvas.width = img.width
    canvas.height = img.height

//canvas画图片

c.drawImage(img, 0, 0, img.width, img.height)

resolve()

}

img.addEventListener('error', (e) => {

reject(e)

})

})

}
 }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
