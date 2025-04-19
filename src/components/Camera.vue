<template>
  <video ref="videoEl" autoplay></video>
</template>

<script>
import { defineComponent, onMounted, ref } from "vue";
export default defineComponent({
  setup() {
    const videoEl = ref(null);

    onMounted(() => {
      if (!videoEl.value) return;

      navigator.mediaDevices
        .getUserMedia({ video: { facingMode: "environment" } })
        .then(function (stream) {
          videoEl.value.srcObject = stream;
          videoEl.value.setAttribute("playsinline", true);
          videoEl.value.play();
        });
    });

    return {
      videoEl,
    };
  },
});
</script>

<style>
* {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
}

video {
    background-color: black;
    width: 100vw;
    height: 100vh;
}
</style>