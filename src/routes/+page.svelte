<script lang="ts">
	import { CardSwiper } from '$lib/CardSwiper';
	import { fade } from 'svelte/transition';

	let swipe: (direction?: 'left' | 'right') => void;

	let people = [
		{
			name: 'Lucas',
			age: 40,
			description: 'Loves to dance in the rain.'
		},
		{
			name: 'Benjamin',
			age: 28,
			description: 'Eats pizza with a fork.'
		},
		{
			name: 'Noah',
			age: 49,
			description: 'Talks to plants.'
		},
		{
			name: 'Emily',
			age: 45,
			description: 'Sleeps with socks on.'
		},
		{
			name: 'Ava',
			age: 43,
			description: 'Thinks they can speak to animals.'
		},
		{
			name: 'Sophia',
			age: 23,
			description: 'Obsessed with organizing.'
		},
		{
			name: 'Charlotte',
			age: 41,
			description: 'Afraid of shadows.'
		},
		{
			name: 'Olivia',
			age: 23,
			description: 'Collects rare pebbles.'
		},
		{
			name: 'Isabella',
			age: 42,
			description: 'Always forgets why they walked into a room.'
		},
		{
			name: 'Jacob',
			age: 24,
			description: 'Can recite movies backwards.'
		}
	];

	let thresholdPassed = 0;
</script>

<div class="h-[100svh] w-[100svw] p-2 flex items-center justify-center overflow-hidden">
	<div class="w-full h-full max-w-xl relative">
		<CardSwiper
			bind:swipe
			cardData={(index) => {
				let i = Math.floor(Math.random() * people.length);
				let j = Math.floor(Math.random() * people.length);
				return {
					title: people[i].name + ', ' + people[i].age,
					description: people[j].description,
					image: `/svelte-swiper-cards/profiles/${index % 14}.png`
				};
			}}
			on:swiped={(e) => {
				console.log(e.detail);
			}}
			bind:thresholdPassed
		/>

		<button
			class="absolute bottom-1 left-1 p-3 px-4 bg-white/50 backdrop-blur-sm rounded-full z-10 text-3xl"
			on:click={() => swipe('left')}
		>
		👎
		</button>
		<button
			class="absolute bottom-1 right-1 p-3 px-4 bg-white/50 backdrop-blur-sm rounded-full z-10 text-3xl"
			on:click={() => swipe('right')}
		>
		👍
		</button>
	</div>

	{#if thresholdPassed !== 0}
		<div
			transition:fade={{ duration: 200 }}
			class="absolute w-full h-full inset-0 bg-white/20 backdrop-blur-sm flex items-center justify-center text-9xl pointer-events-none"
		>
			{thresholdPassed > 0 ? '👍' : '👎'}
		</div>
	{/if}
</div>
