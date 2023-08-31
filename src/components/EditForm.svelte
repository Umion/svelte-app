<script>
	import titleIcon from '$lib/images/title_icon.svg';
	import bgLight from '$lib/images/bg_light.svg';
	import arrowRight from '$lib/images/arrow_right.svg';
	import femaleImage from '$lib/images/female.png';
	import maleImage from '$lib/images/male.png';

	import CustomSelect from '../components/CustomSelect.svelte';
	import CustomSlider from '../components/CustomSlider.svelte';
	import CustomSwitch from '../components/CustomSwitch.svelte';

	import { femaleList, maleList } from '$lib/mockData/';
</script>

<template lang="pug">
.sidebar.sidebar__form
  .form__title
    img(src="{titleIcon}" alt="icon")
    span.font-600 Спадковість
  .form__gender
    .form__gender-label Оберіть стать
    CustomSwitch
  .form__parents
    CustomSelect(
      label="Батько"
      list="{maleList}"
    )
    CustomSelect(
      label="Мати"
      list="{femaleList}"
    )
  .relative
    .form__preview
      img.decor(src="{bgLight}" alt="svg icon light")
      img.form__preview-img(src="{femaleImage}" alt="game character")
      img.form__preview-img.male(src="{maleImage}" alt="game character")
    .form__resemblance
      .form__resemblance-label Схожість
      CustomSlider
  button.form__btn
    span.font-500 Перейти далi
    img(src="{arrowRight}" alt="svg arrow")

</template>

<style lang="scss">
	.sidebar {
		position: relative;
		font-size: 0.95rem;

		&__form {
			padding: 1.13rem 2.2rem 2.22rem;
			width: 33.3rem;
			align-self: stretch;
			overflow: hidden;
		}
		& > *:not(:last-child) {
			margin-bottom: 0.9rem;
		}
	}
	.form {
		&__title {
			display: flex;
			align-items: center;
			padding-bottom: 1.23rem;
			border-bottom: 1px solid rgba(245, 245, 245, 0.01);
			font-size: 1.17rem;

			img {
				width: 0.85rem;
				margin-right: 1.03rem;
			}
		}

		&__gender {
			display: flex;
			align-items: center;
			justify-content: space-between;

			&-label {
				color: #b9b9b9;
			}
		}

		&__parents {
			margin-bottom: 0 !important;
		}

		&__preview {
			position: relative;
			height: 8.33rem;
			background: rgba(245, 245, 245, 0.01);
			backdrop-filter: blur(10px);
			border-radius: 0.38rem;
			display: flex;
			align-items: end;
			justify-content: center;
			margin-bottom: 1rem;
			padding-left: 1rem;

			&-img {
				width: 7.5rem;

				&.male {
					width: 7.8rem;
					transform: translateX(-0.9rem);
				}
			}

			img.decor {
				width: 30rem;
				position: absolute;
				left: 40%;
				top: 50%;
				transform: translate(-50%, -50%);
				pointer-events: none;
				z-index: -1;
			}
		}

		&__resemblance-label {
			color: #b9b9b9;
			margin-bottom: 0.57rem;
		}

		&__btn {
			position: absolute;
			left: 50%;
			transform: translateX(-50%);
			bottom: 2.4rem;
			display: flex;
			align-items: center;
			z-index: 1;
			cursor: pointer;
			background: #ff8a36;
			padding: 1.14rem 2.085rem;
			border-radius: 0.76rem;
			-webkit-box-shadow: 0 0 1.42rem 0 rgba(255, 138, 54, 0.5);
			box-shadow: 0 0 1.42rem 0 rgba(255, 138, 54, 0.5);
			font-size: 1.13rem;

			& img {
				width: 0.5rem;
				margin-left: 1.14rem;
			}
		}
	}
	.relative {
		position: relative;
	}
</style>
