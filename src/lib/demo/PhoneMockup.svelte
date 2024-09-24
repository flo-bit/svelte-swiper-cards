<div class="mx-auto h-[712px] w-[350px] max-w-full rounded-[60px] bg-rose-500 relative">
	<div class="absolute top-20 h-8 w-3 bg-rose-500 -left-0.5 rounded-sm"></div>
	<div class="absolute top-[140px] h-14 w-3 bg-rose-500 -left-[3px] rounded-sm"></div>
	<div class="absolute top-[210px] h-14 w-3 bg-rose-500 -left-[3px] rounded-sm"></div>
	<div class="absolute top-[180px] h-20 w-3 bg-rose-500 -right-[3px] rounded-sm"></div>

	<div class="absolute top-[18px] z-10 flex justify-center w-full">
		<div class="h-7 w-24 bg-black rounded-full"></div>
	</div>

	<div class="absolute top-[180px] h-20 w-3 bg-rose-500 -right-[3px] rounded-sm"></div>

	<div class="absolute inset-0 w-full h-full p-3">
		<div class="bg-rose-200 w-full h-full rounded-[50px] overflow-hidden relative">
			<slot />
		</div>
	</div>
</div>
