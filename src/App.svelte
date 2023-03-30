<script lang="ts">
import * as THREE from 'three';

//create scene and camera

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

//create renderer as big as window
const renderer = new THREE.WebGLRenderer();
//by adding .setSize( window.innerWidth, window.innerHeight, false) you change
//the resolution its supposed to render add
renderer.setSize( window.innerWidth/20, window.innerHeight/20, false);
// add it as DOM Element
document.body.appendChild( renderer.domElement );
renderer.domElement.style = "width:100%;,height:100%;"

//creating the cube 
//it needs geometry, an object, which contains all the vertices and faces of the cube
const geometry = new THREE.BoxGeometry( 2, 1, 1 );
//a material which is just a plain  default material in the color green
const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
//and a mesh. An Object that takes the geometry and applies the material to it accordingly
const cube = new THREE.Mesh( geometry, material );

//add the cube to the scene
scene.add( cube );

//move the camera out as the cube and the camera would be located inside each other 
camera.position.z = 5;

//this will render the screen everytime the screen is refreshed
const animate = () => {
    requestAnimationFrame( animate )
    cube.rotation.x += 0.01
    cube.rotation.y += 0.01
    renderer.render(scene, camera)
}





animate()

</script>

<main>
    <div id="info">Cube?????</div>
</main>

<style lang="scss">
    #info {
	position: absolute;
	top: 10px;
	width: 100%;
	text-align: center;
	z-index: 100;
	display:block;
    color:white;
    font-size: 50px;
    padding-top:200px;
}
</style>
