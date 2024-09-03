<script lang="ts">
	import ClosedFolderIcon from '$lib/icons/ClosedFolderIcon.svelte';
	import OpenedFolderIcon from '$lib/icons/OpenedFolderIcon.svelte';
	import HtmlFileIcon from '$lib/icons/HtmlFileIcon.svelte';

	const htmlFileIcon = HtmlFileIcon;

	let sourceContainerShown = true,
		routeContainerShown = true,
		pageContainerShown = true;

	const showSourceContainer = () => {
		sourceContainerShown = !sourceContainerShown;
	};

	const showRouteContainer = () => {
		routeContainerShown = !routeContainerShown;
	};

	const showPageContainer = () => {
		pageContainerShown = !pageContainerShown;
	};
</script>

<nav class="nav">
	<button class="nav-item" on:click={showSourceContainer}>
		<span>
			<span class="nav-icon-container">
				{#if sourceContainerShown}
					<svelte:component this={OpenedFolderIcon} />
				{:else}
					<svelte:component this={ClosedFolderIcon} />
				{/if}
			</span>
			<span>resume</span>
		</span>
	</button>
	{#if sourceContainerShown}
		<span class="source-container">
			<button class="nav-item" on:click={showRouteContainer}>
				<span>
					<span class="nav-icon-container">
						{#if routeContainerShown}
							<svelte:component this={OpenedFolderIcon} />
						{:else}
							<svelte:component this={ClosedFolderIcon} />
						{/if}
					</span>
					<span>src</span>
				</span>
			</button>
			{#if routeContainerShown}
				<span class="route-container">
					<button class="nav-item" on:click={showPageContainer}>
						<span>
							<span class="nav-icon-container">
								{#if pageContainerShown}
									<svelte:component this={OpenedFolderIcon} />
								{:else}
									<svelte:component this={ClosedFolderIcon} />
								{/if}
							</span>
							<span>routes</span>
						</span>
					</button>
					{#if pageContainerShown}
						<span class="page-container">
							<a class="nav-item about active" href="#about">
								<span>
									<span class="nav-icon-container">
										<svelte:component this={htmlFileIcon} />
									</span>
									<span>about.html</span>
								</span>
							</a>
							<a class="nav-item experience" href="#experience">
								<span>
									<span class="nav-icon-container">
										<svelte:component this={htmlFileIcon} />
									</span>
									<span>experience.html</span>
								</span>
							</a>
							<a class="nav-item highlighted-projects" href="#highlighted-projects">
								<span>
									<span class="nav-icon-container">
										<svelte:component this={htmlFileIcon} />
									</span>
									<span>highlighted-projects.html</span>
								</span>
							</a>
						</span>
					{/if}
				</span>
			{/if}
		</span>
	{/if}
</nav>

<style>
	nav {
		background-color: var(--color-bg-nav);
		box-sizing: border-box;
		border-right: 1px solid var(--color-border);
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		color: var(--color-grey);
		font-size: 0.9em;
		font-weight: 200;
	}

	.source-container,
	.route-container,
	.page-container {
		display: flex;
		flex-direction: column;
	}

	.nav-item {
		width: 300px;
		padding: 6px 0 6px 0;
	}

	nav button {
		cursor: pointer;
		background-color: transparent;
		border: none;
		color: var(--color-grey);
		text-align: left;
		font-weight: 200;
	}

	nav button:hover {
		background-color: var(--color-border);
	}

	nav button span,
	nav a span {
		display: inline-block;
		vertical-align: middle;
	}

	.page-container a {
		text-decoration: none;
		width: 300px;
	}

	.page-container a:hover {
		background-color: var(--color-border);
	}

	.page-container a:active {
		background-color: var(--color-border);
	}

	nav button span,
	nav a span {
		display: inline-block;
		vertical-align: middle;
	}

	.nav-icon-container {
		margin-right: 6px;
	}

	nav > button > span {
		margin-left: 6px;
	}

	.source-container button > span {
		margin-left: 32px;
	}

	.route-container button > span {
		margin-left: 54px;
	}

	.page-container a > span {
		margin-left: 76px;
	}

	.active {
		background-color: var(--color-bg-active);
	}
</style>
