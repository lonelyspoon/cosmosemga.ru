<script>
// You can use import statements here!
//
// More information about how to do this here:
// https://threejs.org/docs/#manual/en/introduction/Import-via-modules

import {
  Scene,
  PerspectiveCamera,
  WebGLRenderer,
  IcosahedronGeometry,
  MeshNormalMaterial,
  Mesh,
} from "three";

import {GLTFLoader} from "three/examples/jsm/loaders/GLTFLoader.js"

const scene = new Scene();
const camera = new PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
);

let loadsign = "Loading"

const loader = new GLTFLoader();
let semga
loader.load(
	'http://localhost:80/3D/scene.gltf',
	function (gltf) {

		semga = gltf.scene.children[0]
		semga.scale.set = (0.25, 0.25, 0.25)
		scene.add(semga)
		function animate() {
  requestAnimationFrame(animate);

  semga.rotation.z += 0.01;

  renderer.render(scene, camera);
}
animate();
loadsign = "Внимание"

	}
)

console.log(loader)




camera.position.z = 25;

const renderer = new WebGLRenderer({ alpha: true });
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);
</script>

<main>
	<h1>{loadsign}!</h1>
	<p>Даша греет кастрюли</p>
	<h2>Спасибо за внимание</h2>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff7300;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	h2 {
		color: #ff7300;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>