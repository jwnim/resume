<script>
	import Nav from '$lib/components/Nav.svelte';
	import Header from '$lib/components/Header.svelte';
	import '../app.css';
</script>

<div class="app-container">
	<div class="nav-container">
		<Nav />
	</div>

	<div class="header-main-container">
		<div class="header-container">
			<Header />
		</div>
		<div class="main-container">
			<slot />
		</div>
	</div>
</div>

<style>
	.app-container {
		display: flex;
	}

	.nav-container {
		min-width: 300px;
		height: 100vh;
		position: -webkit-sticky;
		position: sticky;
		top: 0;
	}

	@media screen and (max-width: 1200px) {
		.nav-container {
			display: none;
		}
	}

	.header-main-container {
		width: 100%;
	}

	.header-container {
		width: 100%;
		position: -webkit-sticky;
		position: sticky;
		top: 0;
	}

	.main-container {
		min-width: 1000px;
		margin: auto;
		width: 50%;
	}

	@media screen and (min-width: 1200px) {
		.main-container {
			min-width: 1000px;
		}
	}

	@media screen and (max-width: 600px) {
		.main-container {
			min-width: 300px;
		}
	}
</style>
