<script>
	import {
		Chart as ChartJS,
		Title,
		Tooltip,
		Legend,
		ArcElement,
		RadialLinearScale,
	} from "chart.js";
	import { onMount } from "svelte";
	import { writable } from "svelte/store";
	import { PolarArea } from "svelte-chartjs";
	ChartJS.register(Title, Tooltip, Legend, ArcElement, RadialLinearScale);
	const countryDataStore = writable([]);
	const dataPolar = {
		datasets: [
			{
				data: [],
				backgroundColor: [],
			},
		],
		labels: [],
	};
	async function fetchCountryData() {
		try {
			const response = await fetch("https://restcountries.com/v3.1/all");
			const data = await response.json();
			const extractedData = data.map((item) => {
				return {
					flag: item?.flags?.svg,
					name: item?.name?.common,
					cioc: item?.cioc ? item?.cioc : "Not Available",
					unMember: item?.unMember,
					currencies: item?.currencies
						? Object.keys(item.currencies)[0]
						: "Not Available",
					populations: item?.population,
					languages: item?.languages,
				};
			});
			countryDataStore.set(extractedData);
			const top10Populations = extractedData
				.sort((a, b) => b.populations - a.populations)
				.slice(0, 10)
				.map((item) => item.populations);
			const top10CountryNames = extractedData
				.sort((a, b) => b.populations - a.populations)
				.slice(0, 10)
				.map((item) => item.name);
			const randomColors = Array.from(
				{ length: 10 },
				() =>
					`rgba(${Math.random() * 255}, ${Math.random() * 255}, ${
						Math.random() * 255
					}, 0.5)`
			);
			console.log(randomColors);
			dataPolar.datasets[0].data = top10Populations;
			dataPolar.datasets[0].backgroundColor = randomColors;
			dataPolar.labels = top10CountryNames;
		} catch (error) {
			console.error("Error fetching data:", error);
		}
	}
	onMount(() => {
		fetchCountryData();
	});
</script>

<section class="p-4">
	<div class="container grid grid-cols-12 gap-6">
		<div class="col-span-12 lg:col-span-8">
			<div class="border-gray-400 border rounded-md overflow-x-scroll">
				<table class="w-full text-center">
					<thead>
						<tr class="border-b border-gray-400">
							<th>Flag</th>
							<th>Name</th>
							<th>CIOC</th>
							<th>UN Member Status</th>
							<th>Currencies (Key)</th>
							<th>Population</th>
							<th>Languages</th>
						</tr>
					</thead>
					<tbody>
						{#each $countryDataStore as country}
							<tr class="border-b border-gray-400">
								<td>
									<img class="w-12" src={country?.flag} alt="Country Flag" />
								</td>
								<td>{country?.name}</td>
								<td>{country?.cioc}</td>
								<td>
									<button
										class="h-50 w-[50px] rounded p-2 {country?.unMember
											? 'bg-gray-300'
											: 'bg-gray-500'}"
									>
										{country?.unMember ? "YES" : "NO"}
									</button>
								</td>
								<td>{country?.currencies}</td>
								<td>{country?.populations}</td>
								<td>
									{#if country?.languages}
										{#each Object.values(country?.languages) as language, index}
											{language}
											{#if index !== Object.keys(country?.languages).length - 1},
											{/if}
										{/each}
									{:else}
										N/A
									{/if}
								</td>
							</tr>
						{/each}
					</tbody>
				</table>
			</div>
		</div>
		<div class="col-span-12 lg:col-span-4">
			<div class="border-gray-400 border rounded-md">
				<h1>Countries</h1>
				<div class="py-6">
					<PolarArea
						data={dataPolar}
						options={{
							responsive: true,
							plugins: {
								legend: {
									position: "bottom",
									title: { display: true, padding: 4 },
									labels: {
										usePointStyle: true,
									},
								},
								tooltip: {
									backgroundColor: "white",
									titleColor: "black",
									callbacks: {
										label: () => {
											return "";
										},
									},
								},
							},
							scales: {
								r: {
									ticks: {
										display: false,
									},
								},
							},
						}}
					/>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	th,
	td {
		@apply p-5;
	}
	h1 {
		@apply p-5 border-gray-400 border-b;
	}
</style>
