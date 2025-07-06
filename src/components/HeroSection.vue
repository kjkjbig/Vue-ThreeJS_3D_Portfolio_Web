<template>
    <canvas
        ref="canvas"
        class="canv"
        :style="`background-image: url(${bgimg})`" />

  </template>
  
  <script setup>
  import { onMounted, ref } from 'vue'
  import * as THREE from 'three'
  import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader'
  
  import big1 from '../assets/big.glb'
  import big2 from '../assets/big2.glb'
  import big3 from '../assets/big3.2.glb'
  import big4 from '../assets/big4.glb'
  
  import bgimg from '../assets/bgimg.png'
  
  const canvas = ref(null)
  
  let camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000)
  camera.position.set(0, 2, 1)
  
  let targetY = camera.position.y
  let targetX = 0
  let targetZ = 1
  
  onMounted(() => {
    const scene = new THREE.Scene()
  
    const renderer = new THREE.WebGLRenderer({
      canvas: canvas.value,
      alpha: true
    })
    renderer.setSize(window.innerWidth, window.innerHeight)
    renderer.setPixelRatio(window.devicePixelRatio)
  
    const light = new THREE.PointLight(0xffffff, 2)
    light.position.set(0, 1.5, -0.1)
    scene.add(light)
  
    const light2 = new THREE.PointLight(0xffffff, 1000)
    light2.position.set(-7, -10, 18)
    scene.add(light2)
  
    const light3 = new THREE.PointLight(0xfde2a9, 10)
    light3.position.set(0, -26, -1)
    scene.add(light3)
  
    const loader = new GLTFLoader()

    loader.load(big1, (gltf) => {
      scene.add(gltf.scene)
    })
  
    loader.load(big2, (gltf) => {
      const model = gltf.scene
      model.scale.set(1, 1, 1)
      model.position.set(1, -12, -0.2)
      model.rotation.y = -0.3
      scene.add(model)
    })
  
    loader.load(big3, (gltf) => {
      const model = gltf.scene
      model.scale.set(1, 1, 1)
      model.position.set(0.5, -22, 9)
      model.rotation.y = 5
      scene.add(model)
    })
  
    loader.load(big4, (gltf) => {
      const model = gltf.scene
      model.scale.set(1, 1, 1)
      model.position.set(0, -31.5, 1.5)
      model.rotation.y = 0
      scene.add(model)
    })
  
    const animate = () => {
      requestAnimationFrame(animate)
  
      camera.position.y = THREE.MathUtils.lerp(camera.position.y, targetY, 0.02)
      camera.position.x = THREE.MathUtils.lerp(camera.position.x, targetX, 0.05)
      camera.position.z = THREE.MathUtils.lerp(camera.position.z, targetZ, 0.05)
  
      renderer.render(scene, camera)
    }
  
    animate()
  
    window.addEventListener('mousemove', (event) => {
      const mouseX = (event.clientX / window.innerWidth) * 2 - 1
      const mouseY = (event.clientY / window.innerHeight) * 2 - 1
  
      targetX = mouseX * 0.05
      targetZ = 1 + mouseY * 0.05
    })
  
    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight
      camera.updateProjectionMatrix()
      renderer.setSize(window.innerWidth, window.innerHeight)
    })
  })
  
  function movecam(num) {
    if (camera) {
      targetY = num
    }
  }
  
  defineExpose({
    movecam
  })
  </script>
  
  <style scoped>

  .canv {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    z-index: -1;
    display: block;
    
  }
  </style>
  