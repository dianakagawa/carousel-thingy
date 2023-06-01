<script lang="ts">
	export let color: string, text: string;
</script>

<div class="w-full h-full flex items-center" style="background-color: {color};">
	<p class="text-white font-bold text-4xl px-8 bg-gray-950 bg-opacity-50">{text}</p>
</div>
