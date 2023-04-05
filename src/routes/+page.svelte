<script lang="ts">
	import { getUserStore } from '$lib/stores/userStore';

	const userStore = getUserStore();
</script>

<h1>Welcome to T3 SvelteKit!</h1>
{$userStore.user?.id}
