<script>
	import { onMount } from 'svelte';

	let input, slider;

	function barStyle() {
		const range = Number(((input.value - input.min) * 100) / (input.max - input.min));

		if (range < 50) {
			slider.style.left = `${range}%`;
			slider.style.right = '50%';
		} else {
			slider.style.right = `${100 - range}%`;
			slider.style.left = '50%';
		}
	}

	onMount(() => {
		input.addEventListener('input', barStyle);
	});
</script>

<template lang="pug">
.slider
  .slider__header
    span Мати
    span Батько
  .slider__body
    input(
      type="range"
      id="volume"
      name="resemblance"
      value="0" 
      min="-50"
      max="50"
      bind:this="{input}"
    )
    .slider__body-bar(bind:this="{slider}")
</template>

<style lang="scss">
	.slider {
		&__header {
			display: flex;
			align-items: center;
			justify-content: space-between;
			margin-bottom: 0.35rem;
		}

		&__body {
			position: relative;

			&-bar {
				position: absolute;
				height: 0.29rem;
				background: #ff8a36;
				right: 50%;
				right: 50%;
				top: 47%;
				pointer-events: none;
				border-radius: 2px;
				-webkit-box-shadow: 0 0 0.7em 0.02rem rgba(255, 217, 7, 0.5);
				box-shadow: 0 0 0.7em 0.02rem rgba(255, 217, 7, 0.5);
				z-index: -1;
			}

			input {
				width: 100%;
				-webkit-appearance: none;
				appearance: none;
				background: rgba(245, 245, 245, 0.1);
				cursor: pointer;
			}
			input::-webkit-slider-runnable-track {
				background: rgba(245, 245, 245, 0.1);
				height: 0.29rem;
				border-radius: 2px;
			}

			input::-webkit-slider-thumb {
				-webkit-appearance: none;
				appearance: none;
				height: 0.95rem;
				width: 0.95rem;
				transform: translateY(-0.33rem);
				background-color: #ff8a36;
				border-radius: 50%;
				-webkit-box-shadow: 0 0 0.7em 0.02rem rgba(255, 217, 7, 0.5);
				box-shadow: 0 0 0.7em 0.02rem rgba(255, 217, 7, 0.5);
			}
		}
	}
</style>
