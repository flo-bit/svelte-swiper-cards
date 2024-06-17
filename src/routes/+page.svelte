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

<div class="bg-white">
	<div class="relative isolate pt-0">
		<svg
			class="absolute inset-0 -z-10 h-full w-full stroke-gray-200 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]"
			aria-hidden="true"
		>
			<defs>
				<pattern
					id="83fd4e5a-9d52-42fc-97b6-718e5d7ee527"
					width="200"
					height="200"
					x="50%"
					y="-1"
					patternUnits="userSpaceOnUse"
				>
					<path d="M100 200V.5M.5 .5H200" fill="none" />
				</pattern>
			</defs>
			<svg x="50%" y="-1" class="overflow-visible fill-gray-50">
				<path
					d="M-100.5 0h201v201h-201Z M699.5 0h201v201h-201Z M499.5 400h201v201h-201Z M-300.5 600h201v201h-201Z"
					stroke-width="0"
				/>
			</svg>
			<rect
				width="100%"
				height="100%"
				stroke-width="0"
				fill="url(#83fd4e5a-9d52-42fc-97b6-718e5d7ee527)"
			/>
		</svg>
		<div
			class="mx-auto max-w-7xl px-6 py-0 flex-col md:flex-row flex md:items-center md:gap-x-10 md:px-8 md:py-12"
		>
			<div class="order-2 md:order-1 mx-auto max-w-2xl md:mx-0 md:flex-auto mb-16 sm:mb-0">
				<h1 class="mt-10 max-w-lg text-4xl font-bold tracking-tight text-gray-900 sm:text-6xl">
					Svelte Swiper Cards
				</h1>
				<p class="mt-6 text-lg leading-8 text-gray-600">
					A swipeable card component for Svelte. Swipe left or right to like or dislike a card.
				</p>
				<div class="mt-10 flex items-center gap-x-6">
					
					<a 
					href="https://github.com/flo-bit/svelte-swiper-cards/"
					target="_blank" class="text-sm font-semibold leading-6 text-red-700"
						>Get code <span aria-hidden="true">→</span></a
					>
				</div>
			</div>
			<div class="mt-8 order-1 sm:mt-8 md:mt-0 md:flex-shrink-0 md:flex-grow">
				<svg
					viewBox="0 0 366 729"
					role="img"
					class="mx-auto w-[22.875rem] max-w-full drop-shadow-xl"
				>
					<title>App screenshot</title>
					<defs>
						<clipPath id="2ade4387-9c63-4fc4-b754-10e687a0d332">
							<rect width="316" height="684" rx="36" />
						</clipPath>
					</defs>
					<path
						fill="#f87171"
						d="M363.315 64.213C363.315 22.99 341.312 1 300.092 1H66.751C25.53 1 3.528 22.99 3.528 64.213v44.68l-.857.143A2 2 0 0 0 1 111.009v24.611a2 2 0 0 0 1.671 1.973l.95.158a2.26 2.26 0 0 1-.093.236v26.173c.212.1.398.296.541.643l-1.398.233A2 2 0 0 0 1 167.009v47.611a2 2 0 0 0 1.671 1.973l1.368.228c-.139.319-.314.533-.511.653v16.637c.221.104.414.313.56.689l-1.417.236A2 2 0 0 0 1 237.009v47.611a2 2 0 0 0 1.671 1.973l1.347.225c-.135.294-.302.493-.49.607v377.681c0 41.213 22 63.208 63.223 63.208h95.074c.947-.504 2.717-.843 4.745-.843l.141.001h.194l.086-.001 33.704.005c1.849.043 3.442.37 4.323.838h95.074c41.222 0 63.223-21.999 63.223-63.212v-394.63c-.259-.275-.48-.796-.63-1.47l-.011-.133 1.655-.276A2 2 0 0 0 366 266.62v-77.611a2 2 0 0 0-1.671-1.973l-1.712-.285c.148-.839.396-1.491.698-1.811V64.213Z"
					/>
					<path
						fill="#dc2626"
						d="M16 59c0-23.748 19.252-43 43-43h246c23.748 0 43 19.252 43 43v615c0 23.196-18.804 42-42 42H58c-23.196 0-42-18.804-42-42V59Z"
					/>
					<foreignObject
						width="316"
						height="684"
						transform="translate(24 24)"
						clip-path="url(#2ade4387-9c63-4fc4-b754-10e687a0d332)"
					>
						<div
							class="h-full w-full p-2 flex items-center justify-center overflow-hidden bg-red-200"
						>
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
					</foreignObject>
				</svg>
			</div>
		</div>
	</div>
</div>

<a
	href="https://github.com/flo-bit/svelte-swiper-cards/"
	target="_blank"
	class="absolute top-0 right-0 bg-white/40 backdrop-blur-sm rounded-bl-xl p-2"
>
	<svg fill="currentColor" viewBox="0 0 24 24" aria-hidden="true" class="w-10 h-10">
		<path
			fill-rule="evenodd"
			d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
			clip-rule="evenodd"
		/>
	</svg>
</a>
