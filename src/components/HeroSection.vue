<template>
    <canvas ref="canvas" class="canv"></canvas>
</template>
    
<script setup>
    import { onMounted, ref } from 'vue'
    import * as THREE from 'three'
    import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader'

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

        // const gridHelper = new THREE.GridHelper(50, 50);
        // scene.add(gridHelper);

        const light = new THREE.PointLight(0xffffff, 2)
        light.position.set(0, 1.5, -0.1)
        scene.add(light)

        const light2 = new THREE.PointLight(0xffffff, 1000)
        light2.position.set(-7, -10, 18)
        scene.add(light2)

        const light3 = new THREE.PointLight(0xfde2a9, 10)
        light3.position.set(0, -26, -1)
        scene.add(light3)

        // const lighthelp = new THREE.PointLightHelper(light3)
        // scene.add(lighthelp)

        const loader = new GLTFLoader()
        loader.load('../src/assets/big.glb', (gltf) => {
            scene.add(gltf.scene)
        })

        loader.load('../src/assets/big2.glb' , (gltf) => {
            const model2 = gltf.scene
            model2.scale.set(1, 1, 1);
            model2.position.set(1, -12, -0.2);
            model2.rotation.y = -0.3
            scene.add(gltf.scene)
        })

        loader.load('../src/assets/big3.2.glb' , (gltf) => {
            const model2 = gltf.scene
            model2.scale.set(1, 1, 1);
            model2.position.set(0.5, -22, 9);
            model2.rotation.y = 5
            scene.add(gltf.scene)
        })

        loader.load('../src/assets/big4.glb' , (gltf) => {
            const model2 = gltf.scene
            model2.scale.set(1, 1, 1);
            model2.position.set(0, -31.5, 1.5);
            model2.rotation.y = 0
            scene.add(gltf.scene)
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

            // ค่าที่ปรับเพื่อให้ขยับพอเหมาะ
            targetX = mouseX * 0.05 // ขยับกล้องซ้าย-ขวา
            targetZ = 1 + mouseY * 0.05 // ขยับกล้องหน้า-หลัง (ลึกเข้า-ออก)
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
    z-index: -1; /* ให้ canvas อยู่ข้างหลัง content */
    display: block;
    background-image: url('../src/assets/bgimg.png');
  }
</style>
  