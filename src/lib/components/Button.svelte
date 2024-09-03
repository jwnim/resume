<script>
	import LinkIcon from '$lib/icons/LinkIcon.svelte';
	import Rusume from '$lib/resume/Resume_Jaewoon_Im.pdf';

	let linkIcon = LinkIcon;
</script>

<a href={Rusume} class="view-button" target="_blank">
	<span>
		<span><svelte:component this={linkIcon} /></span>
		<span>VIEW RESUME</span>
	</span>
</a>

<style>
	.view-button {
		background-color: var(--color-accent);
		color: var(--color-text);
		border: none;
		border-radius: 40px;
		padding: 12px 14px 12px 14px;
		align-items: center;
		cursor: pointer;
		background-size: 200% auto;
		transition: 0.5s;
		box-shadow: 0px 0px 24px -5px var(--color-accent);
		background-image: linear-gradient(
			120deg,
			#a5d9fb 0%,
			var(--color-primary) 10%,
			var(--color-primary) 47%,
			#a5d9fb 50%,
			var(--color-primary) 53%,
			var(--color-primary) 100%
		);
	}

	.view-button:hover {
		background-position: right center;
	}

	.view-button:active {
		transform: scale(0.5);
	}

	.view-button span {
		display: inline-block;
		vertical-align: middle;
		font-family: var(--font-title);
		font-weight: 700;
	}
</style>
