<template>
  <div class="three-demo">
    <div id="container"></div>
  </div>
</template>

<script>
import { LThree } from "../utils/three";
export default {
  name: 'HomeComponent',
  mounted() {
    const three = new LThree('container')
    console.log("three---", three)
    three.initLight()
    three.loadModel('/models/户烘焙缩小模拟OCps贴图.gltf', () => {
      // console.log("progress---", progress)
    }).then((res) => {
      // console.log(three.scene, "模型加载完成---", res.model.scene)
      res.model.scene.scale.set(4.5, 4.5, 4.5)
      three.setModelCenter(res.model.scene)
      three.scene.add(res.model.scene)
    })
  }
}
</script>

<style scoped>

.three-demo {
  width: 80vw;
  height: 56vh;
  margin: 0 auto;
}

#container  {
  width: 100%;
  height: 100%;
  background-color: #f4f4f4;
}
</style>
