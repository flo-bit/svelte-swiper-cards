<script lang="ts">
	import { CardSwiper } from '$lib/CardSwiper';

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
</script>

<svelte:body
	on:keydown={(e) => {
		if (e.key === 'ArrowLeft') {
			swipe('left');
		} else if (e.key === 'ArrowRight') {
			swipe('right');
		}
	}}
/>

<div class="h-[100svh] w-[100svw] p-2 flex items-center justify-center">
	<div class="w-full h-full max-w-xl">
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
		/>

		<button
			class="absolute bottom-1 left-1 p-3 bg-white/50 backdrop-blur-sm rounded-md z-10 border border-white/80"
			on:click={() => swipe('left')}
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				viewBox="0 0 24 24"
				fill="currentColor"
				class="w-6 h-6"
			>
				<path
					d="M15.73 5.5h1.035A7.465 7.465 0 0 1 18 9.625a7.465 7.465 0 0 1-1.235 4.125h-.148c-.806 0-1.534.446-2.031 1.08a9.04 9.04 0 0 1-2.861 2.4c-.723.384-1.35.956-1.653 1.715a4.499 4.499 0 0 0-.322 1.672v.633A.75.75 0 0 1 9 22a2.25 2.25 0 0 1-2.25-2.25c0-1.152.26-2.243.723-3.218.266-.558-.107-1.282-.725-1.282H3.622c-1.026 0-1.945-.694-2.054-1.715A12.137 12.137 0 0 1 1.5 12.25c0-2.848.992-5.464 2.649-7.521C4.537 4.247 5.136 4 5.754 4H9.77a4.5 4.5 0 0 1 1.423.23l3.114 1.04a4.5 4.5 0 0 0 1.423.23ZM21.669 14.023c.536-1.362.831-2.845.831-4.398 0-1.22-.182-2.398-.52-3.507-.26-.85-1.084-1.368-1.973-1.368H19.1c-.445 0-.72.498-.523.898.591 1.2.924 2.55.924 3.977a8.958 8.958 0 0 1-1.302 4.666c-.245.403.028.959.5.959h1.053c.832 0 1.612-.453 1.918-1.227Z"
				/>
			</svg>
		</button>
		<button
			class="absolute bottom-1 right-1 p-3 bg-white/50 backdrop-blur-sm rounded-md z-10 border border-white/80"
			on:click={() => swipe('right')}
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				viewBox="0 0 24 24"
				fill="currentColor"
				class="w-6 h-6"
			>
				<path
					d="M7.493 18.5c-.425 0-.82-.236-.975-.632A7.48 7.48 0 0 1 6 15.125c0-1.75.599-3.358 1.602-4.634.151-.192.373-.309.6-.397.473-.183.89-.514 1.212-.924a9.042 9.042 0 0 1 2.861-2.4c.723-.384 1.35-.956 1.653-1.715a4.498 4.498 0 0 0 .322-1.672V2.75A.75.75 0 0 1 15 2a2.25 2.25 0 0 1 2.25 2.25c0 1.152-.26 2.243-.723 3.218-.266.558.107 1.282.725 1.282h3.126c1.026 0 1.945.694 2.054 1.715.045.422.068.85.068 1.285a11.95 11.95 0 0 1-2.649 7.521c-.388.482-.987.729-1.605.729H14.23c-.483 0-.964-.078-1.423-.23l-3.114-1.04a4.501 4.501 0 0 0-1.423-.23h-.777ZM2.331 10.727a11.969 11.969 0 0 0-.831 4.398 12 12 0 0 0 .52 3.507C2.28 19.482 3.105 20 3.994 20H4.9c.445 0 .72-.498.523-.898a8.963 8.963 0 0 1-.924-3.977c0-1.708.476-3.305 1.302-4.666.245-.403-.028-.959-.5-.959H4.25c-.832 0-1.612.453-1.918 1.227Z"
				/>
			</svg>
		</button>
	</div>
</div>
