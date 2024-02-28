<script setup lang="ts">
import { ref, watchEffect } from "vue";

import * as THREE from "three";
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls.js";

function animate() {
  requestAnimationFrame(animate);

  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;
  if (controls) controls.update();

  if (renderer) renderer.render(scene, camera);
}

function onWindowResize(){
    if (renderer) {

      const canvas = renderer.domElement;
      camera.aspect = canvas.clientWidth / canvas.clientHeight;
      camera.updateProjectionMatrix();
      
      renderer.setSize( canvas.clientWidth, canvas.clientHeight, false);
  }

}

const scene = new THREE.Scene();
scene.add(new THREE.GridHelper(4));

const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
);
camera.position.z = 5;

let renderer: THREE.WebGLRenderer | undefined = undefined;
let controls: OrbitControls | undefined = undefined;
const container = ref<HTMLElement | null>(null);

watchEffect(() => {
  if (container.value) {
    renderer = new THREE.WebGLRenderer({
      canvas: container.value,
    });

    controls = new OrbitControls(camera, renderer.domElement);

    onWindowResize();
  }
});

const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

window.addEventListener( 'resize', onWindowResize, false );

animate();
</script>

<template>
  <canvas 
    ref="container"
    class="w-full h-full"
    @mousedown="() => {}"
  />
</template>

<style scoped></style>
