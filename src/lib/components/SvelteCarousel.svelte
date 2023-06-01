<script lang="ts">
	import Carousel from 'svelte-carousel';
	import Images from './Images.svelte';
	import Colors from './Colors.svelte';
	import { browser } from '$app/environment';

	const colors = [
		{ color: '#00FF00', text: 'Green' },
		{ color: '#0000FF', text: 'Blue' },
		{ color: '#FFFF00', text: 'Yellow' }
	];
	const images = [
		{
			url: 'https://images.unsplash.com/photo-1685462576399-d3a3c11e3f79?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=870&q=80',
			description: 'a person standing on the side of a road'
		},
		{
			url: 'https://images.unsplash.com/photo-1685225263235-74e290ba622b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80',
			description: 'the wing of an airplane flying over a mountain range'
		},
		{
			url: 'https://images.unsplash.com/photo-1685345324402-460a889064d3?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=870&q=80',
			description: 'a clown fish peeking out of a pink sea anemone'
		}
	];
	let carousel: Carousel; // for calling methods of the carousel instance

	const handleNextClick = () => {
		carousel.goToNext();
	};
</script>

{#if browser}
	<div class="mt-8">
		<Carousel bind:this={carousel} let:loaded autoplay autoplayDuration={3000} pauseOnFocus>
			{#each images as src, imageIndex (src)}
				<div class="flex w-full h-80">
					{#if loaded.includes(imageIndex)}
						<Images url={src.url} description={src.description} />
					{/if}
				</div>
			{/each}
		</Carousel>
	</div>

	<button
		class="bg-gray-950 text-white rounded-md px-8 py-1 ml-8 font-bold mb-8"
		on:click={handleNextClick}>Next</button
	>

	<Carousel let:currentPageIndex let:pagesCount let:showPage autoplay autoplayDuration={3000}>
		{#each colors as { color, text } (color)}
			<div class="w-full h-36">
				<Colors {color} {text} />
			</div>
		{/each}
	</Carousel>
{/if}
