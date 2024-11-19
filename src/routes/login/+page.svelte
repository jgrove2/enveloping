<script lang="ts">
	import { signIn } from '@auth/sveltekit/client';
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';

	$effect(() => {
		console.log($page.data)
		if ($page.data.session) {
			console.log("TEST")
			goto('/');
		}
	});
</script>

<h1>Welcome to Budget</h1>

{#if !$page.data.session}
	<h1>You are not logged in</h1>
	<button onclick={() => signIn("github")}>Sign in with Github</button>
{/if}

<style>
	h1 {
		color: var(---text);
	}
</style>
