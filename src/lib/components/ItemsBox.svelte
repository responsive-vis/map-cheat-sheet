<script>
	import { base } from '$app/paths';

	/** @type {string} */
	export let type;

	/** @type {{ groupLabel: string; groupTitle: string; items: Array.<Object>; }} */
	export let data;

	const color = type == 'challenges' ? 'var(--challenge-light)' : 'var(--solution-light)';
</script>

<div class="category" style="--color:{color}">
	<h3><span>{data.groupLabel}</span>{data.groupTitle}</h3>
	{#each data.items as item}
		<div class="item">
			<h4><span>{item.label}</span>{item.text}</h4>
			<img src="{base}/illustrations/{item.img}" alt={item.imgAlt} />
		</div>
	{/each}
</div>

<style>
	div.category {
		border-radius: calc(1rem + 3px);
		height: max-content;
		overflow: hidden; /* so corners don't get cut with background-color */
		box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
		margin-bottom: 0.5rem;
	}

	div.category {
		border: var(--color) 3px solid;
	}

	h3 {
		border-radius: 1rem 1rem 0 0;
		padding: 0 0 0 0.5rem;
		line-height: 1.8rem;
		margin: 0;
		font-size: 1.15rem;
		font-weight: 600;
		background-color: var(--color);
		border-bottom: var(--color) 3px solid;
	}
	h3 span {
		display: inline-block;
		height: 2rem;
		width: 2rem;
		background-color: var(--light-grey);
		border-radius: 1rem;
		margin: 0 0.5rem 0 -0.5rem;
		line-height: 2rem;
		padding: 0;
		text-align: center;
	}

	.item {
		padding: 0.2rem;
		background-color: #fff;
	}
	.category .item:not(:last-child) {
		border-bottom: var(--color) 3px solid;
	}

	h4 {
		font-size: 1rem;
		line-height: 1.3rem;
		font-weight: 400;
		margin: 0;
	}
	h4 span {
		border-radius: 2rem;
		padding: 0 0.25rem 0 0.25rem;
		margin: 0 0.25rem 0 0;
		background-color: var(--color);
	}

	img {
		max-width: min(100%, 300px);
		max-height: 300px;
		min-width: 150px;
		margin: 0.3rem auto;
		display: block;
	}
</style>
