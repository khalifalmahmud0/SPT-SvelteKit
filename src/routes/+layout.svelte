<script>
	import { page } from "$app/stores";
	import "../app.css";
	let menuItems = [
		{ label: "Layout", path: "/" },
		{ label: "Chart", path: "/chart" },
		{ label: "Map", path: "/map" },
	];
</script>

<div class="app">
	<div class="min-h-screen relative font-mono">
		<header id="header" class="container py-8 xl:py-12 text-sm">
			<div
				class="grid grid-cols-2 gap-y-8 justify-items-center md:justify-items-stretch md:items-center"
			>
				<div class="col-span-2 md:col-span-1 text-center md:text-left">
					<a href="/">
						<h1 class="text-3xl font-bold">SPT</h1>
					</a>
				</div>
				<div class="col-span-2 md:col-span-1 text-center md:text-right">
					<code class="font-bold">
						{#each menuItems as menuItem, index}
							<a
								href={menuItem.path}
								class:active={$page.url.pathname === menuItem.path}
							>
								{menuItem.label}
								{#if index !== menuItems.length - 1}
									/
								{/if}
							</a>
						{/each}
					</code>
				</div>
			</div>
		</header>
		<section id="content" class="pt-[25px] pb-[150px]">
			<slot />
		</section>
		<footer id="footer" class="absolute w-full bottom-0 p-8">
			<p class="text-center text-sm tracking-[-0.5px]">
				Feel free to drop a 'hello' @<!-- -->
				<code class="font-bold"> almahmudkhalif@gmail.com </code>
			</p>
		</footer>
	</div>
</div>

<style>
	.active {
		@apply text-neutral-500;
	}
</style>
