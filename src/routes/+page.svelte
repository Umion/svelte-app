<script>
	import EditType from '../components/EditType.svelte';
	import EditForm from '../components/EditForm.svelte';

	import '$lib/styles/global.css';
</script>

<svelte:head>
	<title>Character</title>
	<meta name="description" content="Create character" />
</svelte:head>

<template lang="pug">
.app
  EditType
  EditForm
</template>

<style>
	.app {
		aspect-ratio: 16 / 9;
		/* background-image: url('https://images.unsplash.com/photo-1628114855403-820f62c99e02?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2940&q=80'); */
		background-image: url('../lib/images/bg.jpg');
		background-repeat: no-repeat;
		background-size: cover;

		display: flex;
		justify-content: space-between;
		align-items: center;

		padding: 1.9rem 2.1rem 1.9rem 1.92rem;
	}
</style>
