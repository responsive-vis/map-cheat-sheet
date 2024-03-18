<script>
	import ItemsBox from '$lib/components/ItemsBox.svelte';

	/** @type {number} */
	let windowWidth;

	const challenges = [
		{
			groupLabel: 'C1',
			groupTitle: 'The map becomes unreadable when scaled down.',
			items: [
				{
					label: 'C1.1',
					text: 'Small areas on the map are too small to be visible.',
					img: 'c_small_areas.png',
					imgAlt:
						'Excerpt of a choropleth map of the UK. Two orange circles highlight areas with very small spatial units that are difficult to see.'
				},
				{
					label: 'C1.2',
					text: 'Symbols on the map are too small to be visible.',
					img: 'c_small_symbols.png',
					imgAlt:
						'Proportional circle map showing the Americas. Two orange circles highlight some very small circles that are difficult to see.'
				},
				{
					label: 'C1.3',
					text: 'Symbols overlaid on the map overlap excessively.',
					img: 'c_overlap.png',
					imgAlt:
						'Proportional circle map showing the Americas. An orange circle highlights an area where circles are overlapping heavily.'
				}
			]
		},
		{
			groupLabel: 'C2',
			groupTitle: 'The aspect ratio of the available space does not fit the map.',
			items: [
				{
					label: 'C2.1',
					text: 'The map is very small and surrounded by lots of wasted space.',
					img: 'c_whitespace.png',
					imgAlt:
						'Map of the UK, which is portrait format, scaled to fit a landscape format rectangle. The empty space left and right of the map is highlighted in orange.'
				},
				{
					label: 'C2.2',
					text: 'The map is partly off-screen.',
					img: 'c_offscreen.png',
					imgAlt:
						'Map of the world. A small part of it is visible in a portrait format rectangle representing e.g. a phone screen, the rest of the map is off-screen and this is highlighted by an orange outline.'
				}
			]
		},
		{
			groupLabel: 'C3',
			groupTitle: 'The legend or other UI elements do not fit.',
			items: [
				{
					label: 'C3.1',
					text: 'Legend (text) is too small to read.',
					img: 'c_legend_small.png',
					imgAlt:
						'Choropleth map of the UK. A legend is shown in the top right, but the labels are too small to read.'
				},
				{
					label: 'C3.2',
					text: 'The legend covers part of the map.',
					img: 'c_legend_overlap.png',
					imgAlt:
						'Choropleth map of the UK. A legend with large readable labels is shown in the top right, but it overlaps the map and hides parts of it.'
				}
			]
		}
	];

	const solutions = [
		{
			groupLabel: 'S1',
			groupTitle: 'Start with subtle design changes that will help the map scale down better.',
			items: [
				{
					label: 'S1.1',
					text: 'Maximize the size of the map by repositioning other UI elements.',
					img: 's_maximize_map.png',
					imgAlt:
						'Two wireframes side-by-side. On the left, a sidebar on the top with a small map below it. On the right, the sidebar is on the left and the map is slightly larger to its right.'
				},
				{
					label: 'S1.2',
					text: 'Re-design the legend to be more compact.',
					img: 's_redesign_legend.png',
					imgAlt:
						'Two legend designs side by side. On the left, four colors are listed top to bottom with labels spelling out Category A, through Category D. On the right, four colors are listed side by side and simply labeled A to D, a much more compact design.'
				},
				{
					label: 'S1.3',
					text: 'Replace the legend with annotations or labels on mouseover/tap.',
					img: 's_remove_legend.png',
					imgAlt:
						'An excerpt of a choropleth map with an oversized, symbolic mouse pointer shown on top. The pointer is labelled Category C.'
				},
				{
					label: 'S1.4',
					text: 'Decrease line width or remove outlines where possible.',
					img: 's_decrease_line_width.png',
					imgAlt:
						'Two choropleth map excerpts side-by-side. The left has white outlines for each spatial unit. On the right, the outlines have been removed, making smaller regions more easily readable.'
				},
				{
					label: 'S1.5',
					text: 'Adjust the scale of symbols on the map.',
					img: 's_adjust_scale.png',
					imgAlt:
						'Two proportional circle maps side-by-side. The left one has relatively small circles where some of them are hard to see. On the right, all circles have been scaled up and are easier to see.'
				},
				{
					label: 'S1.6',
					text: 'Change the map projection.',
					img: 's_change_projection.png',
					imgAlt:
						'Two world maps side-by-side. The right one is a little narrower because it uses a different map projection.'
				},
				{
					label: 'S1.7',
					text: 'Displace symbols or spatial units on the edges of the map slightly to make it more compact or to reduce overlap.',
					img: 's_displace_symbols.png',
					imgAlt:
						'Two maps of the UK side-by-side. On the right, Shetland, which is far in the North East of Scotland, i.e. top right corner of the map, has been moved into an inset box beside Scotland. This allows the map to be larger than the map with Shetland in its true position.'
				}
			]
		},
		{
			groupLabel: 'S2',
			groupTitle: 'Make use of scrolling, zooming, and panning.',
			items: [
				{
					label: 'S2.1',
					text: 'Scroll the map vertically.',
					img: 's_scroll_vertically.png',
					imgAlt:
						'A map with some of it off-screen to its top and bottom. A large up and down arrow symbolizes vertical scrolling.'
				},
				{
					label: 'S2.2',
					text: 'Scroll the map horizontally.',
					img: 's_scroll_horizontally.png',
					imgAlt:
						'A map with some of it off-screen to its left and right. A large up and down arrow symbolizes horizontal scrolling.'
				},
				{
					label: 'S2.3',
					text: 'Pan and zoom the entire map.',
					img: 's_pan_zoom.png',
					imgAlt:
						'A map with some of it off-screen in all directions. A large cross of arrows pointing left, right, up and down symbolizes vertical and horizontal panning of the map.'
				},
				{
					label: 'S2.4',
					text: 'Create cutouts that zoom into dense areas.',
					img: 's_cutouts.png',
					imgAlt:
						'A small map of the UK. To its right, a cutout that is zoomed into London is shown.'
				}
			]
		},
		{
			groupLabel: 'S3',
			groupTitle: 'Separate the map into segments.',
			items: [
				{
					label: 'S3.1',
					text: 'Separate the map into equally sized segments.',
					img: 's_segments.png',
					imgAlt:
						'A UK map. To its right, the same map is shown separated into two rectangular sections, created by slicing the map into a top and bottom half.'
				},
				{
					label: 'S3.2',
					text: 'Separate the map into geographic sub-units.',
					img: 's_subunits.png',
					imgAlt:
						'A world map. To its right, six continents are shown arranged into a two by three grid.'
				}
			]
		},
		{
			groupLabel: 'S4',
			groupTitle: 'Use alternative visualization types that allow for more flexible use of space.',
			items: [
				{
					label: 'C4.1',
					text: 'Cartograms & grid maps',
					img: 's_cartograms.png',
					imgAlt:
						'Left: a Dorling cartogram, in which circles are arranged geographically and scaled to represent data points about individual countries. Right: An excerpt of a hexagonal grid map.'
				},
				{
					label: 'C4.2',
					text: 'Geographically ordered visualizations',
					img: 's_geographically_ordered_vis.png',
					imgAlt:
						'A treemap with sections labeled Northern Ireland, Scotland, Wales, England. Rectangles in the treemap are arranged approximately according to their geographic locations.'
				},
				{
					label: 'C4.3',
					text: 'Non-geographic visualizations',
					img: 's_non_geo_vis.png',
					imgAlt: 'Simple bar chart with three bars labeled A, B, and C.'
				},
				{
					label: 'C4.4',
					text: 'Remove visualizations',
					img: 's_no_vis.png',
					imgAlt:
						'Left: lookup search box labeled "Search a country"; the selected country is United Kingdom and the value "Population: 67.0 million" is displayed. Right: A table (schematic, no content).'
				}
			]
		}
	];
</script>

<svelte:window bind:innerWidth={windowWidth} />

<div id="container">
	<header>
		<h1>Responsive Map Cheat Sheet</h1>
		<p>
			This cheat sheet guides you in successfully making your thematic map design responsive to
			different screen sizes and devices. It provides an overview of the most common <b
				>challenges</b
			>, and <b>design solutions</b> to address them. Use the challenges as a checklist to identify potential
			issues, then choose design solutions to address the challenges you identified. The recommendations
			in this cheat sheet are based on guidance from experienced map designers and developers.
		</p>
		<a href="cheatsheet_v1.pdf" target="_blank">Download PDF</a>
	</header>

	<h2 class="challenges">Challenges</h2>
	<p class="guidingQuestion">Which of these are present in your map?</p>
	<div class="challenges">
		{#if windowWidth >= 400 && windowWidth < 600}
			<ItemsBox type="challenges" data={challenges[0]} />
			<div>
				<ItemsBox type="challenges" data={challenges[1]} />
				<ItemsBox type="challenges" data={challenges[2]} />
			</div>
		{:else}
			{#each challenges as challenge}
				<ItemsBox type="challenges" data={challenge} />
			{/each}
		{/if}
	</div>

	<h2 class="solutions">Design Solutions</h2>
	<p class="guidingQuestion">
		Which of these strategies could be useful for your map? <br /> Start with S1, then move on to S2–S4.
	</p>

	<div class="solutions">
		{#if windowWidth >= 600 && windowWidth < 800}
			<ItemsBox type="solutions" data={solutions[0]} />
			<ItemsBox type="solutions" data={solutions[1]} />
			<div>
				<ItemsBox type="solutions" data={solutions[2]} />
				<ItemsBox type="solutions" data={solutions[3]} />
			</div>
		{:else if windowWidth >= 400 && windowWidth < 600}
			<div>
				<ItemsBox type="solutions" data={solutions[0]} />
				<ItemsBox type="solutions" data={solutions[2]} />
			</div>
			<div>
				<ItemsBox type="solutions" data={solutions[1]} />
				<ItemsBox type="solutions" data={solutions[3]} />
			</div>
		{:else}
			{#each solutions as solution}
				<ItemsBox type="solutions" data={solution} />
			{/each}
		{/if}
	</div>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

	:global(:root) {
		--challenge-light: #ffd09c;
		--challenge-dark: #d87506;
		--solution-light: #ebddff;
		--solution-dark: #7516fb;
		--light-grey: #fefefe;
	}

	:global(body, html) {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		font-family: 'Inter', sans-serif;
		background-color: var(--light-grey);
	}

	div#container {
		margin: 0 auto;
		padding: 0 0.5rem;
		max-width: 1000px;
	}

	header {
		padding: 2rem;
		box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
		margin: 2rem auto 0 auto;
		position: relative;
		box-sizing: border-box;
		background: #fff;
		background: linear-gradient(to right, var(--challenge-light), var(--solution-light));
		border-radius: 1rem;
	}
	header a {
		display: block;
		font-weight: bold;
		text-decoration: none;
		color: #000;
		background-color: #fff;
		border-radius: 1rem;
		height: 2rem;
		line-height: 2rem;
		padding: 0 1rem;
		width: fit-content;
	}
	header a:hover {
		box-shadow:
			rgba(0, 0, 0, 0.1) 0px 10px 15px -3px inset,
			rgba(0, 0, 0, 0.1) 0px 4px 6px -4px;
	}

	h1 {
		font-size: 3rem;
		margin: 0 0 0.5rem 0;
	}

	h2 {
		font-size: 2.5rem;
		margin: 2.5rem 0 0.5rem 0;
	}
	h2.challenges {
		color: var(--challenge-dark);
		grid-column: 1/-1; /* from 1st to last col */
	}
	h2.solutions {
		color: var(--solution-dark);
		grid-column: 1/-1;
	}
	p.guidingQuestion {
		font-style: italic;
		grid-column: 1/-1;
	}

	div.challenges,
	div.solutions {
		display: grid;
		grid-template-columns: 1fr;
		column-gap: 0.5rem;
		/* row-gap: 0.5rem; */
		margin: auto;
	}

	@media only screen and (min-width: 400px) {
		/* 2 col layout */
		div.challenges,
		div.solutions {
			grid-template-columns: 1fr 1fr;
		}
	}

	@media only screen and (min-width: 600px) {
		/* 3 col layout */
		div.challenges,
		div.solutions {
			grid-template-columns: 1fr 1fr 1fr;
		}
	}

	@media only screen and (min-width: 800px) {
		/* 4 col layout */
		div.challenges {
			grid-template-columns: 1fr 1fr 1fr;
		}
		div.solutions {
			grid-template-columns: 1fr 1fr 1fr 1fr;
		}
	}
</style>
