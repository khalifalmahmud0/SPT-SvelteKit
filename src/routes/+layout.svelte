<script>
	import "../app.css";
</script>

<div class="app">
	<div class="min-h-screen relative font-mono">
		<header id="header" class="Container py-10 xl:py-12 text-sm">
			<div
				class="grid grid-cols-2 gap-y-8 justify-items-center md:justify-items-stretch md:items-center"
			>
				<div class="col-span-2 md:col-span-1 text-center">
					<!-- <a href="/"
						><img
							alt="Site Logo"
							loading="lazy"
							width="100"
							height="100"
							decoding="async"
							data-nimg="1"
							class="w-52 dark:invert"
							style="color: transparent"
							src="/logo.svg"
						/></a
					> -->
					<h1>Logo Here</h1>
				</div>
				<div class="col-span-2 md:col-span-1 text-center md:text-right">
					<code class="font-bold"
						><a href="/">All Users</a> /<!-- -->
						<a href="/add-user">Add New User</a></code
					>
				</div>
			</div>
		</header>
		<section id="content" class="pt-[25px] pb-[150px]">
			<slot />
		</section>
		<footer id="footer" class="absolute w-full bottom-0 p-10">
			<p class="text-center text-sm tracking-[-0.5px]">
				Feel free to drop a 'hello' @<!-- -->
				<code class="font-bold"> almahmudkhalif@gmail.com </code>
			</p>
		</footer>
	</div>
</div>

<style>
</style>
