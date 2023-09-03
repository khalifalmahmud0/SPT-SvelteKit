<script>
	import { page } from "$app/stores";
	import "../app.css";
	let menuItems = [
		{ label: "Layout", path: "/" },
		{ label: "Chart", path: "/chart" },
		{ label: "Map", path: "/map" },
	];
</script>

<div class="app font-mono">
	<header id="header" class="container py-6 text-sm">
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
	<section id="content">
		<slot />
	</section>
</div>

<style>
	.active {
		@apply text-neutral-500;
	}
</style>
