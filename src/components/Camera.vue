<template>
  <div class="camera-container">
    <video ref="videoEl" autoplay playsinline class="camera-feed"></video>
  </div>

  <div class="form-data">
    <input type="text" />
    <button>Submit</button>
  </div>
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

.camera-container {
  width: 100%;
  height: calc(100vh - 50px);
  position: relative;
}

.camera-container::before {
  content: "";
  background-image: url("https://i.pinimg.com/originals/89/59/5c/89595c967692a040e550ed8f38b99942.png");
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
}
video {
  background-color: black;
  width: 100%;
  height: 100%;
}
.form-data {
    height: 50px;
    display: flex;
}
.form-data input,
.form-data button {
  width: 100%;
  height: 100%;
  border: none;
  background-color: transparent;
  padding: 0 16px;
}

.form-data button {
    text-align: center;
    border: 1px solid;
    max-width: 100px;
}
</style>
