<script>
	import arrowIcon from '$lib/images/arrow_icon.svg';
	import femaleImage from '$lib/images/female.png';

	import { onMount } from 'svelte';

	//props
	export let label;
	export let list;

	let showSelect = false;
	let selected = null;

	onMount(() => {
		console.log('onMount');
		selected = list[0];
	});

	const openSelect = () => {
		showSelect = true;
	};

	function select(person) {
		console.log('click', person);
		selected = person;
		showSelect = false;
	}
</script>

<template lang="pug">
.select(class:spacing="{showSelect}")
  .select__header(
    class:active="{!showSelect}"
    on:click="{openSelect}"
  )
    .select__header-label {label}
    .select__header-button
      span.font-500 {selected && selected.name}
      img(src="{arrowIcon}" alt="svg arrow icon")
  .select__body(class:active="{showSelect}")
    .select__body-title
      .select__body-label {label}
      .select__body-name
        span.font-500 {selected && selected.name}
        img(src="{arrowIcon}" alt="svg arrow icon")
    .select__body-list
      +each('list as person')
        .character(
          class:active="{person.id === selected?.id}"
          on:click!="{(e) => select(person)}"
        )
          .character__img
            img(src="{femaleImage}" alt="character icon")
          p.character__name {person.name}
</template>

<style lang="scss">
	.select {
		position: relative;
		transition: padding 0.7s;

		&.spacing {
			padding-bottom: 19rem;
		}

		&__header {
			display: flex;
			align-items: center;
			justify-content: space-between;

			transform: translateX(-30px);
			opacity: 0;
			pointer-events: none;
			transition: transform 0.7s ease, opacity 0.7s ease;
			margin-bottom: 1.06rem;

			&.active {
				transform: translateX(0px);
				opacity: 1;
				pointer-events: auto;
			}

			&-label {
				color: #b9b9b9;
			}

			&-button {
				width: 9.3rem;
				padding: 0.8rem 0.95rem;
				display: flex;
				align-items: center;
				justify-content: space-between;
				background: rgba(245, 245, 245, 0.05);
				border-radius: 0.38rem;
				cursor: pointer;

				img {
					width: 0.78rem;
				}
			}
		}

		&__body {
			position: absolute;
			left: -2.25rem;
			right: -2.25rem;
			top: 0;
			height: 22rem;
			background: rgba(245, 245, 245, 0.02);
			backdrop-filter: blur(10px);
			transition: transform 0.7s ease, opacity 0.7s ease;
			display: flex;
			flex-direction: column;
			border-radius: 0.38rem;
			padding: 0.6rem 0.76rem 0.6rem 2.25rem;

			transform: translateX(1.4rem);
			opacity: 0;
			pointer-events: none;

			&.active {
				transform: translateX(0);
				opacity: 1;
				pointer-events: auto;
			}

			&-title {
				margin-bottom: 0.71rem;
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding-right: 1.5rem;
			}

			&-label {
				color: #b9b9b9;
			}

			&-name {
				display: flex;
				align-items: center;

				img {
					width: 0.78rem;
					transform: rotate(180deg);
					margin-left: 0.5rem;
				}
			}

			&-list {
				flex-grow: 1;
				display: flex;
				flex-wrap: wrap;
				margin-left: -0.25rem;
				overflow: hidden;
				overflow-y: scroll;

				&::-webkit-scrollbar {
					width: 0.25rem;
				}

				/* Track */
				&::-webkit-scrollbar-track {
					background: rgba(245, 245, 245, 0.07);
				}

				/* Handle */
				&::-webkit-scrollbar-thumb {
					background: #ff8a36;
				}

				/* Handle on hover */
				&::-webkit-scrollbar-thumb:hover {
					background: #fa7b20;
				}
			}
		}
	}

	.character {
		margin: 0 0.25rem 0.71rem;
		cursor: pointer;

		&__img {
			width: 6.66rem;
			aspect-ratio: 1/1;
			margin-bottom: 0.45rem;
			background: rgba(245, 245, 245, 0.05);
			display: flex;
			align-items: end;
			border-radius: 0.3rem;
		}

		&.active .character__img {
			border: 1px solid #ff8a36;
			background: rgba(255, 138, 54, 0.2);
		}

		& img {
			width: 100%;
		}

		&__name {
			text-align: center;
			font-size: 0.86rem;
			color: #ededed;
		}
	}
</style>
