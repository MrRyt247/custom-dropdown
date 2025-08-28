<script lang="ts">
	import { data } from './data/data';

	let selected: string = $state('Select an Item');
	let isOpened: boolean = $state(false);
</script>

<!-- <select value={selected}>
	<option value="" style:display="none">Select an Item</option>
	{#each data as value}
		<option {value}>{value}</option>
	{/each}
</select> -->

<div class="select">
	<div class="select-container" onclick={() => (isOpened = !isOpened)}>
		<span>{selected}</span>
		<span style:rotate={isOpened ? '180deg' : '0deg'}>&downarrow;</span>
	</div>
	<ul style:display={isOpened ? 'flex' : 'none'}>
		{#each data as value}
			<li
				data-value={value}
				data-selected={selected === value ? true : false}
				onclick={() => (selected = value)}
			>
				<span>{value}</span>
				<span style:visibility={selected === value ? 'visible' : 'hidden'}>&check;</span>
			</li>
		{/each}
	</ul>
</div>

<style>
	*,
	*::before,
	*::after {
		box-sizing: border-box;
		margin: 0;
		padding: 0;
	}

	.select {
		display: flex;
		background-color: transparent;
		/* padding: 0.5em 1em; */
		width: 15em;
		border: solid 3px black;
		font-family: inherit;
		font-size: inherit;
		line-height: inherit;
		cursor: pointer;
		border-radius: 10px;
		position: relative;

		.select-container {
			flex-grow: 1;
			padding: 0.5em 1em;
			/* background-color: red; */
			display: inline-flex;
			justify-content: space-between;
		}
	}

	ul {
		flex-direction: column;
		position: absolute;
		top: calc(100% + 1em);
		left: 0;
		width: 100%;
		border: solid 3px black;
		border-radius: 25px;
		overflow: hidden;

		li {
			list-style: none;
			padding: 0.75em 1em;
			border-bottom: solid 3px black;
			display: inline-flex;
			justify-content: space-between;

			/* &:first-child {
				border-radius: 20px 20px 0 0;
			} */

			&:last-child {
				border-bottom: none;
			}

			span:last-child {
				width: 1.25rem;
				height: 1.25rem;
				display: flex;
				align-items: center;
				justify-content: center;
				border-radius: 50%;
				color: white;
				background-color: black;
			}
		}
	}

	/* li[data-selected='true'] {
		background-color: red;
	} */
</style>
