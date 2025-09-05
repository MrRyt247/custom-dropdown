<script lang="ts">
	import { data } from './data/data';
	import '@fontsource/comic-relief';
	import { ChevronDown, Icon } from 'svelte-hero-icons';

	let selected: string = $state(data[0].select);
	let isOpened: boolean = $state(false);
	let dropdownRef: HTMLDivElement;

	function handleClickOutside(event: MouseEvent) {
		if (dropdownRef && !dropdownRef.contains(event.target as Node)) {
			isOpened = false;
		}
	}

	$effect(() => {
		if (isOpened) {
			document.addEventListener('click', handleClickOutside);
		} else {
			document.removeEventListener('click', handleClickOutside);
		}

		return () => {
			document.removeEventListener('click', handleClickOutside);
		};
	});
</script>

<h1 style="margin-bottom: 0.5rem;">Custom Dropdown</h1>

<div class="select" bind:this={dropdownRef}>
	<button type="button" class="select-container" onclick={() => (isOpened = !isOpened)}>
		<span>{selected}</span>
		<span style:rotate={isOpened ? '-180deg' : '0deg'}>
			<Icon src={ChevronDown} size="1.25rem" />
		</span>
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
		font-family: 'Comic Relief', sans-serif;
	}

	.select {
		display: flex;
		width: 18em;
		font-family: inherit;
		font-size: inherit;
		line-height: inherit;
		cursor: pointer;
		position: relative;

		.select-container {
			flex-grow: 1;
			border-radius: 10px;

			span:last-child {
				display: flex;
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
