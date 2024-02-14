# svelte-swiper-cards

Tinder-like swipeable cards for svelte.

> [!NOTE]  
> In active development. Not ready for production.

## Features

- Built with tailwind
- Reuses cards (only two cards, that are swapped)
- Customizable (customize the card)
- Modern: uses @use-gesture/vanilla for gesture handling
- TypeScript

## Installation

- Copy `CardSwiper` folder from `src/libs` to your projects `lib` folder.

- Install dependency

```bash
npm i @use-gesture/vanilla
```

## Usage

```svelte
<script>
	import { CardSwiper } from '$lib/CardSwiper';
</script>

<div class="h-screen w-screen">
	<CardSwiper
		cardData={(index) => {
			return {
				title: 'Card ' + index,
				description: 'Description ' + index
			};
		}}
	/>
</div>
```

### Customize

Customize the `Card.svelte` file to your needs, if you need to pass in more data to your card, edit the `CardData` type in `CardSwiper/index.ts` (and add the prop to `Card.svelte`).

### Programmatic control

You can control the cards programmatically by calling the swipe function.

```svelte
<script>
	import { CardSwiper } from '$lib/CardSwiper';

	let swipe: (direction?: 'left' | 'right') => void;
</script>

<div class="h-screen w-screen">
	<CardSwiper
		cardData={(index) => {
			return {
				title: 'Card ' + index,
				description: 'Description ' + index
			};
		}}
		bind:swipe
	/>
	<button on:click={() => swipe('left')}>Swipe left</button>
	<button on:click={() => swipe('right')}>Swipe right</button>
</div>
```

## Todo

- Events
- Examples
- Refactor
- Testing on multiple devices
- Show optional overlay on cards when swiping

## License

MIT
