<template>
	<div id="vue-animate">
		<div id="blue-box"></div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			movingPathDirection: "right",
		};
	},

	methods: {
		animateSquareBox() {
			const app = document.getElementById("vue-animate");
			let containerWidth = app.offsetWidth;
			let containerHeight = app.offsetHeight;
			let movingByPixel = 10;

			const blueSquareBox = document.getElementById("blue-box");

			let boxLeft = blueSquareBox.offsetLeft;
			let boxTop = blueSquareBox.offsetTop;

			if (boxLeft + 100 >= containerWidth || boxTop + 100 >= containerHeight) {
				this.movingPathDirection = "left";
			} else if (blueSquareBox.offsetLeft < 0) {
				this.movingPathDirection = "right";
			}

			if (this.movingPathDirection === "right") {
				boxLeft = boxLeft + movingByPixel;
				boxTop = boxTop + movingByPixel;
			} else {
				boxLeft = boxLeft - movingByPixel;
				boxTop = boxTop - movingByPixel;
			}

			blueSquareBox.style.left = boxLeft + "px";
			blueSquareBox.style.top = boxTop + "px";
		},
	},

	mounted() {
		setInterval(() => {
			this.animateSquareBox();
		}, 1000);
	},
};
</script>

<style>
#vue-animate {
	position: relative;
	height: 100vh;
}

#blue-box {
	position: absolute;
	height: 100px;
	width: 100px;
	background: blue;
	top: 50px;
	left: 0;
}
</style>
