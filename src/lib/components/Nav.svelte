<script lang="ts">
	import { page } from '$app/stores';
	import { navHeaders } from '$lib/config';
	import type { User } from '$lib/types';
	export let user: User | undefined;
	/*
	 ** $:({url} = $page); reactivally get current page every time it changes.
	 */
	$: ({ url } = $page);
</script>

<div class="container">
	{#if user}
		<div class="user-name">{user.name}</div>
	{/if}
	{#each navHeaders as navItem}
		{#if url.pathname == navItem.url}
			<div class="current-page">{navItem.label}</div>
		{:else}
			<a href={navItem.url}>{navItem.label}</a>
		{/if}
	{/each}
</div>

<style>
	.container {
		display: flex;
		gap: 0.25rem;
	}
	.current-page {
		font-weight: 700;
	}
	.user-name {
		margin-right: 0.5rem;
	}
</style>
