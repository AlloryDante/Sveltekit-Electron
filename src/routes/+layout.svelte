<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';
	interface Props {
		children?: import('svelte').Snippet;
	}

	let { children }: Props = $props();

	let ready: boolean = $state(false);
	onMount(() => (ready = true));
</script>

<div class="dragbar"></div>

{#if ready}
	{@render children?.()}
{/if}

<style>
	.dragbar {
		-webkit-app-region: drag;
		position: absolute;
		z-index: 100;
		height: 40px;
		width: 100%;
	}
</style>
