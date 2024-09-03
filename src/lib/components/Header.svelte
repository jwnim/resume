<header>
	<div class="header-file-name-container">
		<div class="header-file-name">
			<p id="header-file-name">about.html</p>
		</div>
	</div>
	<div class="header-path-name-container"><p id="header-path-name">src/routes/about.html</p></div>
</header>

<style>
	header {
		border-top: 1px solid var(--color-border);
		border-right: 1px solid var(--color-border);
		border-bottom: 1px solid var(--color-border);
		box-sizing: border-box;
		color: var(--color-grey);
		min-width: 100%;
	}

	.header-file-name-container {
		display: flex;
		flex-direction: row;
		background-color: var(--color-bg-nav);
	}

	.header-file-name {
		display: inline-block;
		background-color: var(--color-bg-content);
		border-right: 1px solid var(--color-border);
		box-sizing: border-box;
		padding: 6px 12px 6px 12px;
	}

	.header-file-name p {
		font-size: 0.9em;
		font-weight: 200 !important;
	}

	.header-path-name-container {
		padding: 6px 12px 6px 12px;
		font-family: var(--font-title);
		background-color: var(--color-bg-content);
	}

	.header-path-name-container p {
		font-size: 0.9em !important;
		font-weight: 200 !important;
	}
</style>
