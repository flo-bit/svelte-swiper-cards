<script lang="ts">
	import { onMount } from 'svelte';
	import { DragGesture, type FullGestureState } from '@use-gesture/vanilla';
	import Card from './Card.svelte';
	import type { CardData } from '.';

	let container: HTMLElement;

	let card1: HTMLElement, card2: HTMLElement;
	let card1Data: CardData, card2Data: CardData;

	let cardIndex = 0;

	let topCard: HTMLElement;

	let currentZ = 10000;

	let swiping = false;

	onMount(async () => {
		card1Data = cardData(cardIndex++);
		card2Data = cardData(cardIndex++);

		[card1, card2].forEach(function (el) {
			el.style.zIndex = currentZ.toString();
			currentZ--;

			new DragGesture(el, (state) => {
				onDrag(el, state);
			});
		});

		topCard = card1;
		container.classList.remove('hidden');
	});

	const cardSwiped = (el: HTMLElement, velocity: [number, number], movement: [number, number]) => {
		el.classList.add('transition-transform', 'duration-300');

		var moveOutWidth = document.body.clientWidth;

		var endX = Math.max(Math.abs(velocity[0]) * moveOutWidth, moveOutWidth);
		var toX = movement[0] > 0 ? endX : -endX;
		var endY = Math.abs(velocity[1]) * moveOutWidth;
		var toY = movement[1] > 0 ? endY : -endY;
		var xMulti = movement[0] * 0.03;
		var yMulti = movement[1] / 80;
		var rotate = xMulti * yMulti;

		el.style.transform =
			'translate(' + toX + 'px, ' + (toY + movement[1]) + 'px) rotate(' + rotate + 'deg)';

		setTimeout(() => {
			currentZ--;
			el.style.zIndex = currentZ.toString();

			el.classList.remove('transition-transform', 'duration-300');
			el.style.transform = '';

			if (el === card1) {
				card1Data = cardData(cardIndex++);
				topCard = card2;
			} else {
				card2Data = cardData(cardIndex++);
				topCard = card1;
			}

			swiping = false;
		}, 350);
	};

	const onDrag = (
		el: HTMLElement,
		state: Omit<FullGestureState<'drag'>, 'event'> & {
			event: PointerEvent | MouseEvent | TouchEvent | KeyboardEvent;
		}
	) => {
		swiping = true;
		if (state.pressed) {
			var xMulti = state.movement[0] * 0.03;
			var yMulti = state.movement[1] / 80;
			var rotate = xMulti * yMulti;

			el.style.transform =
				'translate(' +
				state.movement[0] +
				'px, ' +
				state.movement[1] +
				'px) rotate(' +
				rotate +
				'deg)';
		} else {
			var keep = Math.abs(state.movement[0]) < 40 || Math.abs(state.velocity[0]) < 0.5;

			if (keep) {
				el.classList.add('transition-transform', 'duration-300');
				el.style.transform = '';
				setTimeout(() => {
					el.classList.remove('transition-transform', 'duration-300');
				}, 300);
			} else {
				cardSwiped(el, state.velocity, state.movement);
			}
		}
	};

	export const swipe = (direction: 'left' | 'right' = 'right') => {
		cardSwiped(topCard, [direction === 'left' ? -1 : 1, 0.1], [direction === 'left' ? -1 : 1, 1]);
	};

	export let cardData = (index: number): CardData => {
		return {
			title: index.toString(),
			color: index % 2 === 0 ? 'bg-blue-300' : 'bg-green-300',
			description: 'This is card ' + index,
			image: '/profiles/' + (index % 14) + '.png'
		};
	};
</script>

<div class="w-full h-full">
	<div class="w-full h-full relative hidden z-0" bind:this={container}>
		<Card bind:element={card1} {...card1Data} />
		<Card bind:element={card2} {...card2Data} />
	</div>
</div>
