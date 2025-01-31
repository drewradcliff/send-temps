<script lang="ts">
	import { Sun, Wind } from 'lucide-svelte';
	import DialogForm from '../components/dialog-form.svelte';

	let destinations = [
		{
			name: 'Chattanooga',
			weatherDescription: 'Mostly Sunny',
			icon: Sun,
			temperature: 47
		},
		{
			name: 'Red River Gorge',
			weatherDescription: 'Sunny',
			icon: Sun,
			temperature: 38
		},
		{
			name: 'Baraboo',
			weatherDescription: 'Windy',
			icon: Wind,
			temperature: 37
		}
	];
</script>

<h1 class="text-3xl font-semibold">Destinations</h1>
<h2 class="font-light text-zinc-600">Create and manage destinations</h2>
<div class="flex justify-end">
	<DialogForm />
</div>

<div class="py-4"></div>

<div class="flex flex-col gap-4">
	{#each destinations as { name, weatherDescription, icon, temperature }}
		{@const Icon = icon}
		<div class="flex justify-between rounded-2xl border border-zinc-950 p-4">
			<div class="flex flex-col gap-2">
				<h3 class="text-lg font-semibold">{name}</h3>
				<p class="text-sm text-zinc-600">{weatherDescription}</p>
			</div>
			<div class="flex items-start">
				<div class="flex items-center gap-2">
					<Icon class="h-8 w-8" />
					<p class="text-3xl">{temperature}°F</p>
				</div>
			</div>
		</div>
	{/each}
</div>
