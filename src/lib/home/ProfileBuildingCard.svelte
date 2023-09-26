<script lang="ts">
	import { Separator } from '$lib/components/ui/separator';
	import { Button } from '$lib/components/ui/button';
	import * as Card from '$lib/components/ui/card';
	import { Input } from '$lib/components/ui/input';
	import Label from '$lib/components/ui/label/label.svelte';
	import { Badge } from '$lib/components/ui/badge';
	import { CheckCheck, CheckCircle, PackageCheck } from 'lucide-svelte';
	import { Textarea } from '$lib/components/ui/textarea';
	import supabase from '$lib';
	let product = {
		product_name: '',
		prize: '',
		pic_url: '',
		imgs: '',
		desc: '',
		quantity: '',
		owner_name: '',
		owner_email: '',
		owner_domain: ''
	};
	// notify the user that the data is submited
	let isPop = false;
	import * as Alert from '$lib/components/ui/alert';
	import { fly, fade } from 'svelte/transition';
	let submitedData = async () => {
		console.log(product);
		let allimgs = product.imgs.split(',');
		let allimgsarr: any = [];
		allimgs.forEach((img) => {
			allimgsarr.push(img.trim());
		});
		product.imgs = allimgsarr;
		const { data, error } = await supabase.from('products').insert([product]);
		isPop = true;

		setTimeout(() => {
			isPop = false;
		}, 1600);
	};
</script>

<Card.Root>
	<Card.Header class="space-y-1 ">
		<div class="flex justify-between">
			<div>
				<Card.Title class="text-xl">Owner Credentials</Card.Title>
				<Card.Description
					>Enter Your <span class="text-primary">Name, Email, Subdomain</span> for Showcasing the Products</Card.Description
				>
			</div>
			<div>
				<Badge variant="outline" class="border-green-600">Prototype</Badge>
			</div>
		</div>
	</Card.Header>
	<form on:submit|preventDefault={submitedData}>
		<Card.Content class="grid gap-4">
			<div class="grid grid-cols-1 md:grid-cols-2 gap-4">
				<div class="grid gap-2">
					<Label for="name">Name</Label>
					<Input
						id="name"
						type="text"
						placeholder="Your Name"
						name="name"
						bind:value={product.owner_name}
					/>
				</div>
				<div class="grid gap-2">
					<Label for="email">Email</Label>
					<Input
						id="email"
						type="email"
						placeholder="m@example.com"
						name="email"
						bind:value={product.owner_email}
					/>
				</div>
			</div>
			<div class="grid gap-2">
				<Label for="domain">Your Subdomain</Label>
				<Input
					id="domain"
					type="text"
					placeholder="uniqueId : Name, Id"
					name="id"
					bind:value={product.owner_domain}
				/>
			</div>
			<Separator />
			<Card.Header class="m-0 px-0">
				<div class="flex justify-between">
					<div>
						<Card.Title class="text-xl">Product Details</Card.Title>
						<Card.Description class="capitalize"
							>Enter Your Product details to showcase your product</Card.Description
						>
					</div>
					<div>
						<Badge variant="outline" class="border-green-600">Prototype</Badge>
					</div>
				</div>
			</Card.Header>
			<div class="grid grid-cols-1 md:grid-cols-2 gap-4">
				<div class="grid gap-2">
					<Label for="pname">Product Name</Label>
					<Input
						id="pname"
						type="text"
						placeholder="Saffron, Jacket"
						name="name"
						bind:value={product.product_name}
					/>
				</div>
				<div class="grid gap-2">
					<Label for="prize">Product Prize</Label>
					<Input
						id="prize"
						type="text"
						placeholder="3200"
						name="prize"
						bind:value={product.prize}
					/>
				</div>
			</div>
			<div class="grid grid-cols-1 md:grid-cols-2 gap-4">
				<div class="grid gap-2">
					<Label for="pimgurl">Product Image URL</Label>
					<Input
						id="pimgurl"
						type="text"
						placeholder="Image Url of Product"
						name="pimgurl"
						bind:value={product.pic_url}
					/>
				</div>
				<div class="grid gap-2">
					<Label for="quantity">Project Quantity</Label>
					<Input
						id="quantity"
						type="text"
						placeholder="30, 50 Grams"
						name="quantity"
						bind:value={product.quantity}
					/>
				</div>
			</div>
			<div class="grid gap-2">
				<Label for="pallimgs">Project Side Images</Label>
				<Input
					id="pallimgs"
					type="text"
					placeholder="Multiple Image Urls of Product"
					name="pallimgs"
					bind:value={product.imgs}
				/>
			</div>
			<div class="grid gap-2">
				<Label for="desc">Project Description</Label>
				<Textarea
					id="desc"
					placeholder="Define your product qualites like : Exquisite Kashmiri craftsmanship shines in this handwoven textile masterpiece, renowned for its intricate patterns, vibrant colors, and luxurious feel, making it a timeless addition to your home decor."
					name="desc"
					bind:value={product.desc}
				/>
			</div>
		</Card.Content>
		<Card.Footer class="flex justify-end">
			<Button class="w-full md:w-fit">
				{#if product.owner_name && product.owner_email && product.owner_domain}
					<CheckCircle class="mr-2" strokeWidth="1.5" size="20" />
				{/if}
				Submit</Button
			>
		</Card.Footer>
	</form>
</Card.Root>
{#if isPop}
	<div
		in:fly={{ x: 30, duration: 300 }}
		out:fly={{ x: 30, duration: 700 }}
		class="relative hidden md:flex"
	>
		<Alert.Root class="border-green-500 absolute -right-28 bottom-[450px] w-96 shadow-md">
			<CheckCheck strokeWidth="1.4" size="22" />
			<Alert.Title>Uploaded Successfully!</Alert.Title>
			<Alert.Description>Your Product is Uploaded Successfully .</Alert.Description>
		</Alert.Root>
	</div>
{/if}
