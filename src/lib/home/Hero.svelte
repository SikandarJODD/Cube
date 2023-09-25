<script>
	import Button from '$lib/components/ui/button/button.svelte';
	import { PackageSearch,Layout } from 'lucide-svelte';

	let hero = {
		img: 'https://images.pexels.com/photos/16540118/pexels-photo-16540118/free-photo-of-habba-khatoon-mountain-jammu-and-kashmir.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
		title: 'Jammu & Kashmir Products',
		subtext: `Its diverse range of products reflects the region's rich natural resources and artistic heritage`,
		btn1: 'Download',
		btn2: 'Write Your Today'
	};
</script>

<div class="bg-gray-900">
	<div class="relative isolate overflow-hidden">
		<img
			src={hero.img}
			alt="Background"
			class="absolute inset-0 -z-10 h-full w-full object-cover object-center opacity-80 contrast-100"
		/>
		<div class="mx-auto max-w-3xl py-32 sm:py-48 lg:py-40">
			<div
				class="text-center md:border md:border-white px-2 md:p-8 md:backdrop-blur-sm md:hover:backdrop-blur-md transition-all duration-500 md:shadow-lg md:shadow-gray-800/80 rounded-md md:bg-gray-900/20"
			>
				<h1 class="text-4xl font-bold tracking-tight text-white drop-shadow-md sm:text-6xl">
					{hero.title}
				</h1>
				<p class="mt-6 text-lg leading-8 text-gray-100 drop-shadow-md">
					{hero.subtext}
				</p>
				<div class="mt-10 flex items-center justify-center md:gap-x-6 flex-wrap gap-3">
					<Button variant="outline" class='font-semibold hover:text-blue-600' href="/products"
						><PackageSearch class="mr-2" strokeWidth="1.4" /> Products</Button
					>
					<Button variant="outline" class='font-semibold hover:text-blue-600' href="/dashboard"> <Layout  class="mr-2" strokeWidth="1.4"/> Dashboard</Button>
				</div>
			</div>
		</div>
	</div>
</div>
