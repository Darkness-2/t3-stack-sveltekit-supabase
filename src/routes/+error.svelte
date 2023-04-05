<script lang="ts">
	import { page } from '$app/stores';
</script>

<div>
	<span>{$page.status}</span>
	<span>{$page.error?.message}</span>
	{#if $page.error?.errorId}
		<span>Error ID: {$page.error.errorId}</span>
	{/if}
</div>
