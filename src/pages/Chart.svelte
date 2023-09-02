<script>
	let data = [
		{
			Flag: "🇺🇸",
			Name: "United States",
			CIOC: "USA",
			UNMemberStatus: "YES",
			Currencies: "USD",
			Population: "331,915,073",
			Languages: "English, Spanish",
		},
		{
			Flag: "🇨🇦",
			Name: "Canada",
			CIOC: "CAN",
			UNMemberStatus: "NO",
			Currencies: "CAD",
			Population: "38,005,238",
			Languages: "English, French",
		},
		{
			Flag: "🇬🇧",
			Name: "United Kingdom",
			CIOC: "GBR",
			UNMemberStatus: "YES",
			Currencies: "GBP",
			Population: "68,207,116",
			Languages: "English",
		},
		{
			Flag: "🇫🇷",
			Name: "France",
			CIOC: "FRA",
			UNMemberStatus: "YES",
			Currencies: "EUR",
			Population: "65,273,511",
			Languages: "French",
		},
		{
			Flag: "🇩🇪",
			Name: "Germany",
			CIOC: "GER",
			UNMemberStatus: "YES",
			Currencies: "EUR",
			Population: "83,783,942",
			Languages: "German",
		},
	];
</script>

<section class="p-4">
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
				{#each data as item, index}
					<tr
						class={index !== data.length - 1 ? "border-b border-gray-400" : ""}
					>
						<td>{item.Flag}</td>
						<td>{item.Name}</td>
						<td>{item.CIOC}</td>
						<td>
							<button
								class="h-50 w-[50px] rounded p-2 {item.UNMemberStatus === 'YES'
									? 'bg-gray-300'
									: 'bg-gray-500'}">{item.UNMemberStatus}</button
							>
						</td>
						<td>{item.Currencies}</td>
						<td>{item.Population}</td>
						<td>{item.Languages}</td>
					</tr>
				{/each}
			</tbody>
		</table>
	</div>
</section>

<style>
	th,
	td {
		@apply p-5;
	}
</style>
