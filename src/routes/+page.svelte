<script lang="ts">
	import Demo from '$lib/demo/Demo.svelte';
	import PhoneMockup from '$lib/demo/PhoneMockup.svelte';
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
			class="mx-auto max-w-7xl px-6 py-4 flex-col md:flex-row flex md:items-center md:gap-x-10 md:px-8 md:py-12"
		>
			<div class="mx-auto max-w-2xl md:mx-0 md:flex-auto mb-16 sm:mb-0">
				<h1 class="mt-10 max-w-lg text-4xl font-bold tracking-tight text-gray-900 sm:text-6xl">
					Svelte Swiper Cards
				</h1>
				<p class="mt-6 text-lg leading-8 text-gray-600">
					A swipeable card component for Svelte. Swipe left or right to like or dislike a card.
				</p>
				<div class="mt-10 flex items-center gap-x-6">
					<a
						href="https://github.com/flo-bit/svelte-swiper-cards/"
						target="_blank"
						class="text-lg font-semibold leading-6 text-rose-950 bg-rose-400 px-5 py-4 rounded-xl"
						>Get code <span aria-hidden="true">→</span></a
					>
				</div>
				<div class="mt-10 flex items-center gap-x-6">
					<a
						href="https://flo-bit.dev"
						target="_blank"
						class="text-sm font-semibold leading-6 text-rose-700"
						>made by flo-bit</a
					>
				</div>
			</div>
			<div class="sm:mt-8 md:mt-0 md:flex-shrink-0 md:flex-grow scale-75 -mt-32 md:scale-100">
				<PhoneMockup>
					<Demo />
				</PhoneMockup>
			</div>
		</div>
	</div>
</div>

<a
	href="https://github.com/flo-bit/svelte-swiper-cards/"
	target="_blank"
	class="absolute top-0 right-0 bg-white/40 backdrop-blur-sm rounded-bl-xl p-3"
>
	<svg fill="currentColor" viewBox="0 0 24 24" aria-hidden="true" class="w-9 h-9">
		<path
			fill-rule="evenodd"
			d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
			clip-rule="evenodd"
		/>
	</svg>
</a>
