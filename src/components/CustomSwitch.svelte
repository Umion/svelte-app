<script>
	import iconMale from '$lib/images/icon_male.svg';
	import iconFemale from '$lib/images/icon_female.svg';

	let value = false;
</script>

<template lang="pug">
.switch
  input(id="switch" bind:checked="{value}" type="checkbox")
  label(class="slider" for="switch")
    .switch__slider
    .switch__img
      img.lg(src="{iconMale}" class:active="{!value}" alt="svg icon")
    .switch__img
      img(src="{iconFemale}" class:active="{value}" alt="svg icon")

</template>

<style lang="scss">
	.switch {
		& input {
			display: none;
		}

		& label {
			position: relative;
			padding: 0.23rem 0.4rem;
			background: rgba(245, 245, 245, 0.05);
			border-radius: 0.57rem;
			display: flex;
			cursor: pointer;
		}

		&__img {
			width: 3.6rem;
			height: 3.42rem;
			display: flex;
			align-items: center;
			justify-content: center;

			& img {
				width: 34%;
				opacity: 0.5;
				transition: opacity 0.4s;

				&.lg {
					width: 1.6rem;
				}

				&.active {
					opacity: 1;
				}
			}
		}

		&__slider {
			position: absolute;
			top: 0.23rem;
			left: 0.4rem;
			width: 3.6rem;
			height: 3.41rem;
			background-color: #ff8a36;
			-webkit-transition: left 0.4s;
			transition: left 0.4s;
			z-index: -1;
			border-radius: 0.57rem;

			-webkit-box-shadow: 0px 0px 19px -3px rgba(255, 138, 54, 0.5);
			box-shadow: 0px 0px 19px -3px rgba(255, 138, 54, 0.5);
		}

		& input:checked + label .switch__slider {
			left: calc(0.4rem + 3.6rem);
		}
	}
</style>
