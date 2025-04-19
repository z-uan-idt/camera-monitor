<template>
  <Camera msg="Hello Vue 3 in CodeSandbox!" />
</template>

<script>
import Camera from "./components/Camera.vue";

export default {
  name: "App",
  components: {
    Camera: Camera,
  },
};
</script>