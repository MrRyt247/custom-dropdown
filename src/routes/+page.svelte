<script lang="ts">
	import { data } from './data/data';

	let selected: string = $state(data[0].select);
	let isOpened: boolean = $state(false);
</script>

<div class="select">
	<button type="button" class="select-container" onclick={() => (isOpened = !isOpened)}>
		<span>{selected}</span>
		<span style:rotate={isOpened ? '-180deg' : '0deg'}>&downarrow;</span>
	</button>
	<ul style:display={isOpened ? 'flex' : 'none'}>
		{#each data as item}
			{#each item.options as value}
				<button
					type="button"
					{value}
					onclick={() => {
						selected = value;
						isOpened = !isOpened;
					}}
				>
					<span>{value}</span>
					<span style:visibility={selected === value ? 'visible' : 'hidden'}>&check;</span>
				</button>
			{/each}
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
		width: 15em;
		font-family: inherit;
		font-size: inherit;
		line-height: inherit;
		cursor: pointer;
		position: relative;

		.select-container {
			flex-grow: 1;
			border-radius: 10px;

			span:last-child {
				transition: rotate 300ms ease;
			}
		}
	}

	button {
		padding: 0.5em 1em;
		border: solid 3px black;
		background-color: transparent;
		padding: 0.75em 1em;
		display: inline-flex;
		justify-content: space-between;
	}

	ul {
		flex-direction: column;
		position: absolute;
		top: calc(100% + 1em);
		left: 0;
		width: 100%;
		border: solid 3px black;
		border-radius: 20px;
		overflow: hidden;

		> button {
			border: none;
			border-bottom: solid 3px black;

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
</style>
