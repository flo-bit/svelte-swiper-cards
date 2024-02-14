# svelte-swiper-cards

Tinder-like swipeable cards for svelte.

> [!NOTE]  
> Still in active development. Expect breaking changes.

[Try the demo here!](https://flo-bit.github.io/svelte-swiper-cards/)

https://github.com/flo-bit/svelte-swiper-cards/assets/45694132/61077605-b6f8-4114-aaa3-5527d8887f99

## Features

- Built with tailwind
- Reuses cards (only two cards, that are swapped)
- Customizable (customize the card)
- Modern: uses @use-gesture/vanilla for gesture handling
- TypeScript

## Installation

- You need to have tailwind installed in your project, see [here for installation instructions](https://tailwindcss.com/docs/guides/sveltekit).

- Copy the `CardSwiper` folder from `src/libs` to your projects `lib` folder.

- Install dependency

```bash
npm i @use-gesture/vanilla
```

## Usage

```svelte
<script>
  import { CardSwiper } from '$lib/CardSwiper'

  let data = (index) => {
    return {
      title: 'Card ' + index,
      description: 'Description ' + index
    }
  }
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
<script>
  import { CardSwiper } from '$lib/CardSwiper'

  let swipe: (direction?: 'left' | 'right') => void
</script>

<div class="h-screen w-screen">
  <CardSwiper bind:swipe />
  <button on:click={() => swipe('left')}>Swipe left</button>
  <button on:click={() => swipe('right')}>Swipe right</button>
</div>
```

### Events

```svelte
<script>
  import { CardSwiper } from '$lib/CardSwiper'

  function onSwipe(event) {
    // details: 
    // direction: 'left' | 'right'
    // index: number
    // element: HTMLElement
    // data: CardData
    console.log(event.details)
  }
</script>

<div class="h-screen w-screen">
  <CardSwiper on:swipe={onSwipe} />
</div>
```

### Other props

Show a threshold overlay when swiping like so (set to 0 if no threshold reached, 1 if right threshold, -1 if left threshold is reached):

```svelte
<script>
  import { CardSwiper } from '$lib/CardSwiper'

  let thresholdPassed = 0
</script>

<CardSwiper bind:thresholdPassed />

{#if thresholdPassed !== 0}
  <div class="absolute w-full h-full inset-0 flex items-center justify-center text-9xl">
    {thresholdPassed > 0 ? '👍' : '👎'}
  </div>
{/if}
```

You can also set the minimum threshold as a percentage of the card width (default is 0.5) and the minimum speed (default is 0.5).

```svelte
<CardSwiper
  minSwipeDistance={0.3}
  minSwipeVelocity={0.3}
/>
```

Per default Cards can be swiped with Arrow keys, too. You can disable this by setting `arrowKeys` to `false`.

## License

MIT
