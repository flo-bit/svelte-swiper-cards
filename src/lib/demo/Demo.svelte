<script lang="ts">
	import { CardSwiper, type SwipeEventData } from '$lib/CardSwiper';
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';

	import people from './people.json';

	onMount(() => {
		// preload images
		for (let i = 0; i < 14; i++) {
			let img = new Image();
			img.src = `/svelte-swiper-cards/profiles/${i}.webp`;
		}
	});

	let swipe: (direction?: 'left' | 'right') => void;
	let thresholdPassed = 0;

	function onSwipe(cardInfo: SwipeEventData) {
		console.log('swiped', cardInfo.direction, 'on card', cardInfo.data.title);
	}

	function cardData(index: number) {
		let i = Math.floor(Math.random() * people.length);
		let j = Math.floor(Math.random() * people.length);
		return {
			title: people[i].name + ', ' + people[i].age,
			description: people[j].description,
			image: `/svelte-swiper-cards/profiles/${index % 14}.webp`
		};
	}
</script>

<div class="h-full w-full p-2 flex items-center justify-center relative overflow-hidden">
	<div class="w-full h-full max-w-xl relative">
		<CardSwiper bind:swipe bind:thresholdPassed {cardData} {onSwipe} />

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
