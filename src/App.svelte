<script lang="ts">
import * as THREE from 'three';
import {GLTFLoader} from "three/examples/jsm/loaders/GLTFLoader"


const scene = new THREE.Scene()
const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000)
const renderer = new THREE.WebGLRenderer()
renderer.setSize(window.innerWidth/5, window.innerHeight/5, false)
document.body.appendChild(renderer.domElement)
renderer.domElement.style.height = "100%"
renderer.domElement.style.width = "100%"



const geometry = new THREE.ConeGeometry(1.5,1.5,3)
const material = new THREE.MeshBasicMaterial()
const cube = new THREE.Mesh(geometry,material)


camera.position.z = 5

const backGroundColor = new THREE.Color(0x000000)


const amongium = new THREE.TextureLoader().load("/src/assets/amongus.jpeg")
amongium.wrapS = THREE.RepeatWrapping
amongium.wrapT = THREE.RepeatWrapping
amongium.repeat.set(3,1)
amongium.rotation = -0.155
material.map = amongium

scene.background = backGroundColor




scene.add(cube)

const animate = () => {
    requestAnimationFrame( animate )
    cube.rotation.y += 0.01
    renderer.render(scene, camera)
}

animate()




</script>

<main>
    <div id="info">Sus????????ß</div>
</main>

<style lang="scss">
    #info {
	position: absolute;
	top: 10px;
	width: 100%;
	text-align: center;
	z-index: 100;
	display:block;
    font-size: 50px;
    padding-top:200px;
    color: white;
}
</style>
