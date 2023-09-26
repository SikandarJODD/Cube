<script>
	import supabase from '$lib';
	import Button from '$lib/components/ui/button/button.svelte';
	import { Circle } from 'lucide-svelte';
	import { onMount } from 'svelte';
	$: allitems = [];
	onMount(async () => {
		const { data, error } = await supabase.from('products').select('*');
		if (error) console.log(error);
		else {
			allitems = data;
		}
	});
	$: console.log(allitems);
</script>

<div class="bg-white py-6 sm:py-8 lg:py-12">
	<div class="mx-auto max-w-screen-2xl px-4 md:px-8">
		<!-- text - start -->
		<div
			class="mb-10 md:mb-16 rounded-md overflow-hidden contrast-125 h-32 flex items-center justify-end px-3 md:px-10 border border-slate-800 shadow-sm shadow-gray-800/60"
			style="background-image: url('https://img.freepik.com/free-vector/background-template-with-mandala-pattern-design_1308-44444.jpg?w=1060&t=st=1695676191~exp=1695676791~hmac=8f9ef614bf2db6f692b258d44ed8abb98fcf2aeac73025133a093e3b40a61964'); background-size: cover; background-position: center;"
		>
			<h2
				class=" text-right text-2xl font-bold lg:text-5xl drop-shadow-xl shadow-gray-900 text-blue-700"
			>
				Jammu & Kashmir Products
			</h2>

			<!-- <p class="mx-auto max-w-screen-md text-center text-gray-500 md:text-lg">
				This is a section of some simple filler text, also known as placeholder text. It shares some
				characteristics of a real written text but is random or otherwise generated.
			</p> -->
		</div>
		<!-- text - end -->

		<div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 lg:gap-6">
			<!-- product - start -->
			{#each allitems as item}
				<div class="border border-slate-800 rounded-xl overflow-hidden h-fit group">
					<a href="/products/{item.id}" class="group relative block h-96 overflow-hidden rounded-t-lg bg-gray-100">
						<img
							src={item.pic_url}
							loading="lazy"
							alt={item.product_name}
							class="h-full w-full object-cover object-top transition duration-200 group-hover:scale-110 opacity-90 group-hover:opacity-100"
						/>
					</a>

					<div class="flex items-start justify-between  gap-2 rounded-b-lg bg-gray-100 p-4">
						<div class="flex flex-col">
							<a
								href="/products/{item.id}"
								class="font-bold text-gray-800 transition duration-100 hover:text-gray-500 lg:text-md line-clamp-2 group-hover:text-gray-950"
								>{item.product_name}</a
							>
							<span class="text-sm text-gray-500 lg:text-base capitalize">by {item.owner_name}</span>
						</div>

						<div class="flex flex-col items-end ">
							<span class="font-bold text-gray-600 lg:text-md group-hover:text-blue-600"
								>₹{item.prize}.00</span
							>
						</div>
					</div>
				</div>
			{/each}
			<!-- product - end -->
		</div>
	</div>
</div>
