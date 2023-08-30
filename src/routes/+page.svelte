<script>
	import '$lib/styles/global.css';
	import type1 from '$lib/images/type1.svg';
	import type2 from '$lib/images/type2.svg';
	import type3 from '$lib/images/type3.svg';
</script>

<svelte:head>
	<title>Character</title>
	<meta name="description" content="Create character" />
</svelte:head>

<div class="app">
	<div class="sidebar">
		<img src={type1} alt="" />
		<img src={type2} alt="" />
		<img src={type3} alt="" />
	</div>
	<div class="sidebar" />
</div>

<style>
	.app {
		aspect-ratio: 16 / 9;
		background-image: url('https://images.unsplash.com/photo-1628114855403-820f62c99e02?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2940&q=80');
		background-repeat: no-repeat;
		background-size: cover;

		display: flex;
		justify-content: space-between;
		align-items: center;

		padding: 1.9rem;
	}
	.sidebar {
		width: 5rem;
		height: 300px;
		background: #f5f5f505;
		backdrop-filter: blur(10px);
		padding: 0.76rem;
		border-radius: 0.76rem;
	}
	.sidebar img {
		width: 100%;
	}
</style>
