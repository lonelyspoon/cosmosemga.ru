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

const loader = new GLTFLoader();

loader.load(
	'3D/popa.gltf',
	function (gltf) {
		scene.add(gltf.scene)
	}
)

console.log(loader)


const geometry = new IcosahedronGeometry();
const material = new MeshNormalMaterial();
const mesh = new Mesh(geometry, material);
scene.add(mesh);



camera.position.z = 5;

const renderer = new WebGLRenderer({ alpha: true });
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

function animate() {
  requestAnimationFrame(animate);

  mesh.rotation.x += 0.01;
  mesh.rotation.y += 0.01;

  renderer.render(scene, camera);
}
animate();
</script>

<main>
	<h1>{name}!</h1>
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