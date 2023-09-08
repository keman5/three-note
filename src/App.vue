<template>
  <canvas id="canvas" />
</template>

<script setup>
  import { onMounted } from 'vue';
  import * as THREE from 'three';

  onMounted(() => {
    const canvas = document.getElementById("canvas");

    // 创建3D场景
    const scene = new THREE.Scene();
    // 创建立方体
    const cube = new THREE.BoxGeometry(1, 1, 1);
    // 设置立方体表面颜色
    const material = new THREE.MeshBasicMaterial({
      color: '#1890ff',
    });
    // 生成物体对象
    const mesh = new THREE.Mesh(cube, material);

    scene.add(mesh);

    // 创建观察场景的相机
    const camera = new THREE.OrthographicCamera(-4, 4, 4, -4); // 正交相机

    // 设置相机位置
    camera.position.set(2, 2, 3); // 相机默认的坐标是在(0,0,0);
    // 将相机添加到场景中
    scene.add(camera);

    // 创建渲染器
    const renderer = new THREE.WebGLRenderer({
      canvas,
    });

    // 设置渲染器大小
    renderer.setSize(window.innerWidth, window.innerHeight);
    // 执行渲染
    renderer.render(scene, camera);
  });
</script>

<style>
  *{margin:0;
    padding:0;
  }
  #app{height: 100vh;}
  #canvas{
    width: 100vw;
    height: 100vh;
  }
</style>
