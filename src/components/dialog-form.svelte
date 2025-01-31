<script lang="ts">
	import { Check, XIcon } from 'lucide-svelte';
	import { Checkbox, Dialog, Label, Slider } from 'bits-ui';

	let temperatureSliderValue = [40, 80];
	let humiditySliderValue = [50];
	let rainSliderValue = [30];
	let windSliderValue = [10];

	function getWindCategory(speed: number): string {
		if (speed === 0) return 'Calm';
		if (speed <= 7) return 'Light breeze';
		if (speed <= 31) return 'Moderate wind';
		if (speed <= 61) return 'Strong wind';
		if (speed >= 75) return 'Hurricane';
		return 'Severe storm';
	}
</script>

<Dialog.Root>
	<Dialog.Trigger
		class="rounded-lg bg-zinc-950 px-4 py-2 text-white hover:cursor-pointer hover:bg-zinc-800"
		>Add destination</Dialog.Trigger
	>
	<Dialog.Portal>
		<Dialog.Overlay class="fixed inset-0 z-50 bg-black/80" />
		<Dialog.Content
			class="fixed top-[50%] left-[50%] z-50 -translate-x-[50%] -translate-y-[50%] rounded-lg border border-zinc-950 bg-white p-5 shadow-lg sm:max-w-[490px] md:w-full"
		>
			<Dialog.Title class="pb-2 text-2xl font-semibold">Add destination</Dialog.Title>
			<Dialog.Description class="pb-4 text-sm text-zinc-600"
				>Add a new destination to your list</Dialog.Description
			>
			<Label.Root for="location" class="text-sm font-semibold">Location</Label.Root>
			<input
				id="location"
				placeholder="Enter location"
				type="text"
				name="location"
				class="w-full rounded-lg border border-zinc-950 p-2"
			/>
			<div class="py-4"></div>
			<Label.Root for="temperature" class="text-sm font-semibold"
				>Ideal temperature range</Label.Root
			>
			<Slider.Root
				bind:value={temperatureSliderValue}
				let:thumbs
				class="relative flex w-full touch-none items-center pt-4 select-none"
			>
				<span class="relative h-2 w-full overflow-hidden rounded-full bg-zinc-200">
					<Slider.Range class="absolute h-full bg-zinc-950" />
				</span>
				{#each thumbs as thumb}
					<Slider.Thumb
						class=" block size-[25px] cursor-pointer rounded-full border bg-white shadow"
						{thumb}
					/>
				{/each}
			</Slider.Root>
			<div class="mt-2 flex justify-between text-sm text-zinc-600">
				<span>{temperatureSliderValue[0]}°F</span>
				<span>{temperatureSliderValue[1]}°F</span>
			</div>
			<div class="py-4"></div>
			<Label.Root for="humidity" class="text-sm font-semibold">Max humidity</Label.Root>
			<Slider.Root
				bind:value={humiditySliderValue}
				let:thumbs
				class="relative flex w-full touch-none items-center pt-4 select-none"
			>
				<span class="relative h-2 w-full overflow-hidden rounded-full bg-zinc-200">
					<Slider.Range class="absolute h-full bg-zinc-950" />
				</span>
				{#each thumbs as thumb}
					<Slider.Thumb
						class=" block size-[25px] cursor-pointer rounded-full border bg-white shadow"
						{thumb}
					/>
				{/each}
			</Slider.Root>
			<div class="mt-2 flex justify-between text-sm text-zinc-600">
				<span>{humiditySliderValue[0]}%</span>
			</div>
			<div class="py-4"></div>
			<Label.Root for="rain" class="text-sm font-semibold">Max chance of rain</Label.Root>
			<Slider.Root
				bind:value={rainSliderValue}
				let:thumbs
				class="relative flex w-full touch-none items-center pt-4 select-none"
			>
				<span class="relative h-2 w-full overflow-hidden rounded-full bg-zinc-200">
					<Slider.Range class="absolute h-full bg-zinc-950" />
				</span>
				{#each thumbs as thumb}
					<Slider.Thumb
						class=" block size-[25px] cursor-pointer rounded-full border bg-white shadow"
						{thumb}
					/>
				{/each}
			</Slider.Root>
			<div class="mt-2 flex justify-between text-sm text-zinc-600">
				<span>{rainSliderValue[0]}%</span>
			</div>
			<div class="py-4"></div>
			<Label.Root for="wind" class="text-sm font-semibold">Max wind speed</Label.Root>
			<Slider.Root
				bind:value={windSliderValue}
				let:thumbs
				class="relative flex w-full touch-none items-center pt-4 select-none"
			>
				<span class="relative h-2 w-full overflow-hidden rounded-full bg-zinc-200">
					<Slider.Range class="absolute h-full bg-zinc-950" />
				</span>
				{#each thumbs as thumb}
					<Slider.Thumb
						class=" block size-[25px] cursor-pointer rounded-full border bg-white shadow"
						{thumb}
					/>
				{/each}
			</Slider.Root>
			<div class="mt-2 flex justify-between text-sm text-zinc-600">
				<span>{windSliderValue[0]} mph ({getWindCategory(windSliderValue[0])})</span>
			</div>
			<div class="py-4"></div>
			<div class="flex flex-col space-y-3">
				<span class="text-sm leading-none font-semibold">Weekend warrior</span>
				<div class="flex items-center space-x-3">
					<Checkbox.Root
						id="weekend-warrior"
						class="inline-flex size-[25px] items-center justify-center rounded-md border bg-white"
					>
						<Checkbox.Indicator let:isChecked class="inline-flex items-center justify-center">
							{#if isChecked}
								<Check class="size-[15px]" />
							{/if}
						</Checkbox.Indicator>
					</Checkbox.Root>
					<Label.Root for="weekend-warrior" class="text-sm text-zinc-600"
						>Get notified only on the weekends</Label.Root
					>
				</div>
			</div>
			<div class="py-4"></div>
			<div class="flex justify-end">
				<Dialog.Close
					class="rounded-lg bg-zinc-950 px-4 py-2 text-white hover:cursor-pointer hover:bg-zinc-800"
					>Create</Dialog.Close
				>
			</div>
			<Dialog.Close class="absolute top-5 right-5 cursor-pointer">
				<XIcon class="size-5" />
			</Dialog.Close>
		</Dialog.Content>
	</Dialog.Portal>
</Dialog.Root>
