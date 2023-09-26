<script>
	import {
		BarChart2,
		LayoutGrid,
		PackageCheck,
		ShieldCheck,
		Target,
		TrendingUp
	} from 'lucide-svelte';

	let allfeatues = [
		{
			name: 'Growth',
			desc: ' Expand product range, optimize site performance, harness data insights, invest in marketing, improve customer service, and embrace emerging technologies',
			icon: TrendingUp
		},
		{
			name: 'Flexible Layout',
			desc: 'Allows businesses to add, edit, and organize product listings with details such as images, prices, and descriptions.',
			icon: LayoutGrid
		},
		{
			name: 'Goal Oriented',
			desc: 'Maximize online sales, enhance user experience, drive customer retention, and achieve sustainable growth through efficient operations and strategic marketing.',
			icon: Target
		},
		{
			name: 'Speed',
			desc: 'Enables Producres to create and manage Business, such as selling saffron, artwork and other useful products, to engage customers.',
			icon: BarChart2
		},
		{
			name: 'Security',
			desc: 'Implements security measures like SSL certificates and fraud detection tools to protect customer data and prevent unauthorized transactions.',
			icon: ShieldCheck
		},
		{
			name: 'Quality Product',
			desc: 'Offers various shipping methods, calculates shipping costs, and provides tracking information to customers.',
			icon: PackageCheck
		}
	];
</script>

<div class="bg-white py-6 sm:py-8 lg:py-12 mt-4">
	<div class="mx-auto max-w-screen-2xl px-4 md:px-16">
		<!-- text - start -->
		<div class="mb-10 md:mb-16">
			<h2 class="mb-4 text-center text-2xl font-bold text-gray-800 md:mb-6 lg:text-4xl">
				Our competitive advantage
			</h2>
		</div>
		<!-- text - end -->

		<div class="grid gap-8 sm:grid-cols-2 md:gap-12 xl:grid-cols-3 xl:gap-10">
			{#each allfeatues as item}
				<div class="flex gap-4 md:gap-6 border hover:border-slate-500 hover:bg-zinc-200/40 transition-all duration-200 group rounded-xl p-4 ">
					<div
						class="flex h-12 w-12 shrink-0 items-center justify-center rounded-lg bg-indigo-500 text-white shadow-lg md:h-14 md:w-14 md:rounded-xl group-hover:transform group-hover:scale-110 transition-all duration-200"
					>
						<svelte:component this={item.icon} />
					</div>

					<div>
						<h3 class="mb-2 text-lg font-semibold md:text-xl  group-hover:text-gray-950 transition-all duration-200">{item.name}</h3>
						<p class="mb-2 text-gray-500 group-hover:text-gray-800">
							{item.desc}
						</p>
					</div>
				</div>
			{/each}
		</div>
	</div>
</div>
