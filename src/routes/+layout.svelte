<script lang="ts">
	import '../app.css';
	import { browser } from '$app/environment';
	import { QueryClient, QueryClientProvider } from '@tanstack/svelte-query';
	import { createUserStore } from '$lib/stores/userStore';
	import { setContext } from 'svelte';

	const queryClient = new QueryClient({
		defaultOptions: {
			queries: {
				enabled: browser
			}
		}
	});

	/**
	 * Create the userStore and attach it to a context.
	 * Ensures stores are unique per request.
	 * See https://kit.svelte.dev/docs/state-management#using-stores-with-context
	 */
	const userStore = createUserStore();
	setContext('userStore', userStore);
</script>

<QueryClientProvider client={queryClient}>
	<main>
		<slot />
	</main>
</QueryClientProvider>
