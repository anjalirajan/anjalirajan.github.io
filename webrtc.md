<html>
<video autoplay></video>
<img src="">
<canvas style="display:none;"></canvas>
</html>
<script>
const captureVideoButton = document.querySelector(
  "#screenshot .capture-button"
);
const screenshotButton = document.querySelector("#screenshot-button");
const img = document.querySelector("#screenshot img");
const video = document.querySelector("#screenshot video");

const canvas = document.createElement("canvas");

captureVideoButton.onclick = function () {
  navigator.mediaDevices
    .getUserMedia(constraints)
    .then(handleSuccess)
    .catch(handleError);
};

screenshotButton.onclick = video.onclick = function () {
  canvas.width = video.videoWidth;
  canvas.height = video.videoHeight;
  canvas.getContext("2d").drawImage(video, 0, 0);
  // Other browsers will fall back to image/png
  img.src = canvas.toDataURL("image/webp");
};

function handleSuccess(stream) {
  screenshotButton.disabled = false;
  video.srcObject = stream;
}
</script>
