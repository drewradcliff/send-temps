<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>

<div class="mx-auto max-w-md pt-10">
	{@render children()}
</div>
