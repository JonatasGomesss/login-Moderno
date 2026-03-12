<script setup>
  import * as THREE from 'three'
  import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js'
  import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js'
  import { onMounted } from 'vue'

  onMounted(() => {
    const scene = new THREE.Scene()
    scene.background = new THREE.Color(0x11_11_11)

    const camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth / window.innerHeight,
      0.1,
      1000,
    )

    camera.position.set(0, 2, 6)

    const renderer = new THREE.WebGLRenderer({ antialias: true })
    renderer.setSize(window.innerWidth, window.innerHeight)
    document.body.append(renderer.domElement)

    // iluminação
    const ambientLight = new THREE.AmbientLight(0xff_ff_ff, 0.7)
    scene.add(ambientLight)

    const directionalLight = new THREE.DirectionalLight(0xff_ff_ff, 1)
    directionalLight.position.set(5, 10, 5)
    scene.add(directionalLight)

    // chão
    const floorGeometry = new THREE.PlaneGeometry(20, 20)
    const floorMaterial = new THREE.MeshStandardMaterial({ color: 0x22_22_22 })
    const floor = new THREE.Mesh(floorGeometry, floorMaterial)

    floor.rotation.x = -Math.PI / 2
    floor.position.y = -1

    scene.add(floor)

    // controles de câmera
    const controls = new OrbitControls(camera, renderer.domElement)
    controls.enableDamping = true

    // loader do carro
    const loader = new GLTFLoader()

    loader.load('/src/assets/models/carro.glb', gltf => {
      const car = gltf.scene

      car.scale.set(1, 1, 1)
      car.position.y = -1

      scene.add(car)
    })

    // animação
    function animate () {
      requestAnimationFrame(animate)

      controls.update()

      renderer.render(scene, camera)
    }

    animate()

    // responsivo
    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight
      camera.updateProjectionMatrix()

      renderer.setSize(window.innerWidth, window.innerHeight)
    })
  })
</script>

<template>
  <div />
</template>
