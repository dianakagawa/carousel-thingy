<script lang="ts">
	export let url: string, description: string;
</script>

<div
	style="background-image: url({url})"
	class="w-full h-full bg-center bg-cover flex items-center"
>
	<p class="text-white font-bold text-4xl px-8 bg-gray-950 bg-opacity-50">
		{description}
	</p>
</div>
