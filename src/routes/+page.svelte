<svelte:head>
	<style>
		@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
	</style>
</svelte:head>

<header>
	<h1>Responsive Map Cheat Sheet</h1>
	<p>
		This cheat sheet guides you in successfully making your map design responsive. It provides an
		overview of the most common <span class="highlight challenge">challenges</span>, and
		<span class="highlight solution">design solutions</span> to address them. The recommendations in
		this cheat sheet are based on guidance from experienced map designers and developers.
	</p>
</header>

<div class="challenges">
	<h2>Challenges</h2>
	<p class="guidingQuestion">Which of these are present in your map?</p>
	<div class="category c1">
		<h3><span>C1</span>Scaling the map down makes it unreadable.</h3>
		<div class="item">
			<h4><span>C1.1</span>Small areas on the map are too small to be visible.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="/illustrations/c_small_areas.png" />
		</div>
		<div class="item">
			<h4><span>C1.2</span>Symbols on the map are too small to be visible.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="/illustrations/c_small_symbols.png" />
		</div>
		<div class="item">
			<h4><span>C1.3</span>Symbols overlaid on the map overlap excessively.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="/illustrations/c_overlap.png" />
		</div>
	</div>
	<div class="category c2">
		<h3><span>C2</span>The aspect ratio of the available space is mismatched with the map.</h3>
		<div class="item">
			<h4><span>C2.1</span>The map is very small and surrounded by lots of wasted space.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="/illustrations/c_whitespace.png" />
		</div>
		<div class="item">
			<h4><span>C2.2</span>The map is partly off-screen.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/c_offscreen.png" />
		</div>
	</div>
	<div class="category c3">
		<h3><span>C3</span>Legend or other UI elements do not fit.</h3>
		<div class="item">
			<h4><span>C3.1</span>Legend (text) is too small to read.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/c_legend_small.png" />
		</div>
		<div class="item">
			<h4><span>C3.2</span>The legend covers part of the map.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/c_legend_overlap.png" />
		</div>
	</div>
</div>

<div class="solutions">
	<h2>Design Solutions</h2>
	<p class="guidingQuestion">
		Which of these strategies could be useful for your map? Start with S1, then move on to S2–S4.
	</p>
	<div class="category s1">
		<h3>
			<span>S1</span>Start with subtle design changes that will help the map scale down better.
		</h3>
		<div class="item">
			<h4><span>S1.1</span>Maximize the size of the map by repositioning other UI elements.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_maximize_map.png" />
		</div>
		<div class="item">
			<h4><span>S1.2</span>Re-design the legend to be more compact.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_redesign_legend.png" />
		</div>
		<div class="item">
			<h4><span>S1.3</span>Replace the legend with annotations or labels on mouseover/tap.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_remove_legend.png" />
		</div>
		<div class="item">
			<h4><span>S1.4</span>Decrease line width or remove outlines where possible.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_decrease_line_width.png" />
		</div>
		<div class="item">
			<h4><span>S1.5</span>Adjust the scale of symbols on the map.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_adjust_scale.png" />
		</div>
		<div class="item">
			<h4><span>S1.6</span>Change the map projection.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_change_projection.png" />
		</div>
		<div class="item">
			<h4>
				<span>S1.7</span>Displace symbols or spatial units on the edges of the map slightly to make
				it more compact or to reduce overlap.
			</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_displace_symbols.png" />
		</div>
	</div>
	<div class="category s2">
		<h3><span>S2</span>Make use of scrolling, zooming, and panning.</h3>
		<div class="item">
			<h4><span>S2.1</span>Scroll the map vertically.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_scroll_vertically.png" />
		</div>
		<div class="item">
			<h4><span>S2.2</span>Scroll the map horizontally.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_scroll_horizontally.png" />
		</div>
		<div class="item">
			<h4><span>S2.3</span>Pan and zoom the entire map.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_pan_zoom.png" />
		</div>
		<div class="item">
			<h4><span>S.2.4</span>Create cutouts that zoom into dense areas.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_cutouts.png" />
		</div>
	</div>
	<div class="category s3">
		<h3><span>S3</span>Separate the map into segments.</h3>
		<div class="item">
			<h4><span>S3.1</span>Separate the map into equally sized segments.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_segments.png" />
		</div>
		<div class="item">
			<h4><span>S3.2</span>Separate the map into geographic sub-units.</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_subunits.png" />
		</div>
	</div>
	<div class="category s4">
		<h3>
			<span>S4</span>Use alternative visualization types that allow for more flexible use of space,
			such as:
		</h3>
		<div class="item">
			<h4><span>C4.1</span>Cartograms & grid maps</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_cartograms.png" />
		</div>
		<div class="item">
			<h4><span>C4.2</span>Geographically ordered visualizations</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_geographically_ordered_vis.png" />
		</div>
		<div class="item">
			<h4><span>C4.3</span>Non-geographic visualizations</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_non_geo_vis.png" />
		</div>
		<div class="item">
			<h4><span>C4.4</span>Remove visualizations</h4>
			<!-- svelte-ignore a11y-missing-attribute -->
			<img src="illustrations/s_no_vis.png" />
		</div>
	</div>
</div>

<style>
	:root {
		--challenge-light: #ffd09c;
		--challenge-dark: #d87506;
		--solution-light: #ebddff;
		--solution-dark: #7516fb;
		--light-grey: #f1f1f1;
	}

	:global(body, html) {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	header {
		background-color: var(--light-grey);
		padding: 1rem;
	}

	div,
	p,
	h1,
	h2,
	h3,
	h4 {
		font-family: 'Inter', sans-serif;
	}

	.challenges h2 {
		color: var(--challenge-dark);
	}
	.solutions h2 {
		color: var(--solution-dark);
	}
	p.guidingQuestion {
		font-style: italic;
		text-align: right;
	}

	div.challenges,
	div.solutions {
		display: grid;
		column-gap: 3px;
	}
	div.challenges {
		grid-template-columns: 1fr 1fr 1fr;
	}
	div.solutions {
		grid-template-columns: 1fr 1fr 1fr 1fr;
	}

	div.category {
		border-radius: calc(1.25rem + 3px);
		height: max-content;
	}
	.challenges div.category {
		border: var(--challenge-light) 3px solid;
	}
	.solutions div.category {
		border: var(--solution-light) 3px solid;
	}
	.c1,
	.s1 {
		grid-column-start: 1;
	}
	.c2,
	.s2 {
		grid-column-start: 2;
	}
	.c3,
	.s3 {
		grid-column-start: 3;
	}
	.s4 {
		grid-column-start: 4;
	}

	h3 {
		border-radius: 1.25rem 1.25rem 0 0;
		margin: 0;
		line-height: 2.5rem;
		padding: 0;
	}
	.challenges h3 {
		background-color: var(--challenge-light);
		border-bottom: var(--challenge-light) 3px solid;
	}
	.solutions h3 {
		background-color: var(--solution-light);
		border-bottom: var(--solution-light) 3px solid;
	}
	h3 span {
		display: inline-block;
		height: 2.5rem;
		width: 2.5rem;
		background-color: var(--light-grey);
		border-radius: 1.25rem;
		margin: 0;
		line-height: 2.5rem;
		padding: 0;
		text-align: center;
		margin-right: 0.4rem;
	}

	.item {
		padding: 0.2rem;
	}
	.challenges .item:not(:last-child) {
		border-bottom: var(--challenge-light) 3px solid;
	}
	.solutions .item:not(:last-child) {
		border-bottom: var(--solution-light) 3px solid;
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
	}
	.challenges h4 span {
		background-color: var(--challenge-light);
	}
	.solutions h4 span {
		background-color: var(--solution-light);
	}

	span.highlight.challenge {
		background-color: var(--challenge-light);
	}
	span.highlight.solution {
		background-color: var(--solution-light);
	}
	span.highlight {
		font-weight: 700;
		border-radius: 2rem;
		padding: 0 0.25rem 0 0.25rem;
		margin: 0 -0.25rem 0 -0.25rem;
	}

	img {
		max-width: min(100%, 300px);
		max-height: 300px;
		min-width: 150px;
		margin: 0.3rem auto;
		display: block;
	}
</style>
