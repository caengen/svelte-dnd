<script>
	import { onMount } from 'svelte';

    let canvas;

	function trackMouse({ x, y, type }) {
    if (type === "mousedown") {
      mouseDown = true;
    }
    if (type === "mouseup") {
      mouseDown = false;
    }
    if (mouseDown) {
      mousePos.x = x;
      mousePos.y = y;
      drawImage(x, y);
    }
  }
  function drawImage(x, y) {
    const dimensions = 200;
    const ctx = canvasElement.getContext("2d");
    ctx.drawImage(
      imgElement,
      x - dimensions / 2,
      y - dimensions,
      dimensions,
      dimensions
    );
  }
  function resetDrawing() {
    coords = [];
    const ctx = canvasElement.getContext("2d");
    ctx.clearRect(0, 0, windowWidth, windowHeight);
  }
  onMount(() => {
    const ctx = canvasElement.getContext("2d");
  });
</script>

<style>
	div {
	background-size: 32px 32px;
    background-image: linear-gradient(to right, grey 1px, transparent 1px), linear-gradient(to bottom, grey 1px, transparent 1px);
	width: 513px;
	height: 513px;
	}
	canvas {
		background-color: transparent;
	}
</style>

<div>
	<canvas
		on:mousemove={trackMouse}
		on:mouseup={trackMouse}
		on:mousedown={trackMouse}
		bind:this={canvas}
	></canvas>
</div>