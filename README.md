# svelte-swiper-cards

Tinder-like swipeable cards component for svelte.

[Try the demo here!](https://flo-bit.github.io/svelte-swiper-cards)

https://github.com/flo-bit/svelte-swiper-cards/assets/45694132/61077605-b6f8-4114-aaa3-5527d8887f99

## Features

- Built with **tailwind**
- **Reuses cards** (only two cards, that are swapped)
- **Customizable** (easily customize the card ui and data)
- **Modern**: uses @use-gesture/vanilla for gesture handling
- Uses **TypeScript**

## Installation

- You need to have tailwind installed in your project, see [here for installation instructions](https://tailwindcss.com/docs/guides/sveltekit).

- Download the [`CardSwiper`](https://download-directory.github.io/?url=https%3A%2F%2Fgithub.com%2Fflo-bit%2Fsvelte-swiper-cards%2Ftree%2Fmain%2Fsrc%2Flib%2FCardSwiper) folder from `src/libs` to your projects `src/lib` folder.

- Install dependency `@use-gesture/vanilla`

```bash
npm i @use-gesture/vanilla
```

## Usage

```svelte
<script lang="ts">
	import { CardSwiper } from '$lib/CardSwiper';

	// function that returns the data for each card, by default has title, description and image
	let data = (index) => {
		return {
			title: 'Card ' + index,
			description: 'Description ' + index,
			image: '/profiles/' + index + '.webp'
		};
	};
</script>

<div class="h-screen w-screen">
	<CardSwiper cardData={data} />
</div>
```

### Customize

Customize the `Card.svelte` file to your needs, if you need to pass in more data to your card, edit the `CardData` type in `CardSwiper/index.ts` (and add the prop to `Card.svelte`).

### Programmatic control

You can control the cards programmatically by calling the swipe function.

```svelte
<script lang="ts">
	import { CardSwiper } from '$lib/CardSwiper';

	let swipe: (direction?: 'left' | 'right') => void;
</script>

<div class="h-screen w-screen">
	<CardSwiper bind:swipe />
	<button on:click={() => swipe('left')}>Swipe left</button>
	<button on:click={() => swipe('right')}>Swipe right</button>
</div>
```

### Events

```svelte
<script lang="ts">
	import { CardSwiper } from '$lib/CardSwiper';

	function onSwipe(cardInfo: {
		direction: Direction;
		element: HTMLElement;
		data: CardData;
		index: number;
	}) {
		console.log('swiped', cardInfo.direction, 'on card', cardInfo.data.title);
	}
</script>

<div class="h-screen w-screen">
	<CardSwiper {onSwipe} />
</div>
```

### Other props

#### thresholdPassed

Show a threshold overlay when swiping like so (set to 0 if no threshold reached, 1 if right threshold, -1 if left threshold is reached):

```svelte
<script>
	import { CardSwiper } from '$lib/CardSwiper';

	let thresholdPassed = 0;
</script>

<CardSwiper bind:thresholdPassed />

{#if thresholdPassed !== 0}
	<div class="absolute w-full h-full inset-0 flex items-center justify-center text-9xl">
		{thresholdPassed > 0 ? '👍' : '👎'}
	</div>
{/if}
```

#### minSwipeDistance, minSwipeVelocity

You can also set the minimum threshold as a percentage of the card width (default is 0.5) and the minimum speed (default is 0.5).

```svelte
<CardSwiper minSwipeDistance={0.3} minSwipeVelocity={0.3} />
```

#### arrowKeys

Per default Cards can be swiped with Arrow keys, too. You can disable this by setting `arrowKeys` to `false`.

#### anchor

if you want the user to just be able to move the card left or right in a curve, set the anchor to a high number (at least 1000, recommended >5000).

## License

MIT
