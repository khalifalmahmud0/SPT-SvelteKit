<script>
</script>

<section>
	<div
		class="grid grid-rows-12 md:grid-rows-6 grid-cols-4 md:grid-cols-12 h-screen md:h-full grid-flow-row md:grid-flow-col"
	>
		<div
			class="bg-blue-400 text-center col-span-4 row-span-3 order-1 md:col-span-2 md:row-span-3 md:order-1"
		/>
		<div
			class="bg-teal-400 text-center col-span-4 row-span-3 order-2 md:col-span-2 md:row-span-2 md:order-2"
		/>
		<div
			class="bg-fuchsia-400 text-center col-span-4 row-span-3 order-5 md:col-span-6 md:row-span-1 md:order-3"
		/>
		<div
			class="bg-rose-100 text-center col-span-4 row-span-3 order-3 md:col-span-4 md:row-span-5 md:order-4"
		/>
		<div
			class="bg-blue-500 text-center col-span-4 row-span-3 order-6 md:col-span-6 md:row-span-2 md:order-5"
		/>
		<div
			class="bg-yellow-100 text-center grid justify-center content-center col-span-4 row-span-3 order-4 md:col-span-4 md:row-span-4 md:order-6"
		>
			<div
				class=" grid justify-center content-center w-[300px] h-[300px] m-16 bg-[#293462]"
			>
				<div
					class="mountain_circle w-[200px] h-[200px] bg-yellow-100 rounded-full"
				>
					<div class="main_mountain1" />
					<div class="main_mountain2" />
				</div>
			</div>
		</div>
		<div
			class="bg-emerald-400 text-center col-span-4 row-span-3 order-7 md:col-span-2 md:row-span-4 md:order-7"
		/>
	</div>
</section>

<style>
	.mountain_circle {
		position: relative;
		overflow: hidden;
	}
	.main_mountain1 {
		position: absolute;
		content: "";
		bottom: 0px;
		left: -40px;
		border-top: 0px solid transparent;
		border-right: 70px solid transparent;
		border-bottom: 70px solid #fe5f55;
		border-left: 70px solid transparent;
		z-index: 5;
	}
	.main_mountain2 {
		position: absolute;
		content: "";
		bottom: 0px;
		left: 10px;
		border-top: 0px solid transparent;
		border-left: 130px solid transparent;
		border-bottom: 130px solid #fe5f55;
		border-right: 120px solid transparent;
		z-index: 5;
	}
</style>
