<template>
  <div class="home">
    <div id="viewer"></div>
  </div>
</template>

<script setup>
import { ref , reactive , onMounted} from 'vue'
import { Viewer } from 'photo-sphere-viewer' // 引入插件
import 'photo-sphere-viewer/dist/photo-sphere-viewer.css' //引入CSS样式
// 全景视图
const  panoramaViewer = ref(null)
const img = ref(require('../assets/BJ.png'))
// 全景图初始化
const initViewer = async function () {
  panoramaViewer.value = new Viewer({
    container: document.querySelector('#viewer'), // 容器
    panorama: img.value, // 全景图片地址
    navbar: [
      'autorotate',
      'zoom',
      'caption',
      'fullscreen'
    ],
    plugins: [], // 标记点
    size: {
      width: '100%',
      height: '100%'
    }
  })
}

onMounted(() => {
  initViewer()
})

</script>

<style scoped>
.home{
  width: 100%;
  height: 100%;
}
</style>
