<script>
	import { page } from '$app/stores';
	import tab_routes from '$lib/constants/tab_routes';

	$: p_name = $page.url.pathname;
</script>

<div role="navigation">
	<ul role="tablist">
		{#each tab_routes as { label, link }}
			<li role="presentation">
				<a href={link} role="tab" aria-selected={p_name == link ? 'true' : null}>
					<span>{label}</span>
				</a>
			</li>
		{/each}
	</ul>
</div>

<style lang="scss">
	div {
		view-transition-name: nav;
	}
	ul {
		display: grid;
		width: 100%;
		grid-auto-flow: column;
		grid-auto-columns: 1fr;
		align-items: center;
		font-size: var(--step-0);
		line-height: 2;
	}
	li {
		display: block;
	}
	a {
		display: flex;
		align-items: center;
		justify-content: center;
		font-weight: 700;
		width: 100%;
		height: 100%;

		color: var(--soverlay);

		&:focus-visible,
		&:hover {
			background: var(--surface);
			outline: 0;
		}
	}

	[aria-selected='true'] {
		color: var(--text);
		span {
			view-transition-name: tab-nav;
			border-bottom: 4px solid var(--mauve);
		}
	}
</style>
