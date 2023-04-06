<script lang="ts">
	import { trpc } from '$lib/client/trpc';
	import { getUserStore } from '$lib/stores/userStore';
	import { createQuery } from '@tanstack/svelte-query';

	const userStore = getUserStore();

	const helloQuery = createQuery({
		queryKey: ['hello'],
		queryFn: () => trpc.hello.query()
	});
</script>

<h1>Welcome to T3 SvelteKit!</h1>
<p>User ID: {$userStore.user?.id}</p>

{#if $helloQuery.isLoading}
	<p>Loading tRPC...</p>
{:else if !$helloQuery.data}
	<p>Something went wrong...</p>
{:else}
	<p>Greeting: {$helloQuery.data}</p>
{/if}
