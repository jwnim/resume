<script>
	export let skill;
</script>

<span class="badge">
	{skill}
</span>

<style>
	.badge {
		background-color: var(--color-primary);
		border: none;
		border-radius: 40px;
		padding: 6px 12px 6px 12px;
		white-space: nowrap;
		font-weight: 700;
		background-size: 200% auto;
		transition: 0.5s;
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

	.badge:hover {
		background-position: right center;
	}
</style>
