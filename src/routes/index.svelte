<script lang="ts">
	let price: string = '';
	let charge: string = '';
	let operatingCost: string = '';
	let grade: string = '';
	let interest: string = '';
	let amortizationRate: string = '2';
	let other: string = '';

	const replaceCommas = (value: string) => value.replace(/,/g, '.').replace(/\s/g, '');

	const handleSubmit = () => {
		const lendingAmount = Number(replaceCommas(price)) * (Number(replaceCommas(grade)) / 100);
		const amortizationAmount =
			(lendingAmount * (Number(replaceCommas(amortizationRate)) / 100)) / 12;
		const interestAmount = (lendingAmount * (Number(replaceCommas(interest)) / 100) * 0.7) / 12;
		const operatingCostAmount = Number(replaceCommas(operatingCost)) / 12;
		const chargeAmount = Number(replaceCommas(charge));
		const otherAmount = Number(replaceCommas(other));

		// console.log({
		// 	lendingAmount,
		// 	amortizationAmount,
		// 	interestAmount,
		// 	operatingCostAmount,
		// 	chargeAmount,
		// 	otherAmount
		// });

		const cost =
			amortizationAmount + interestAmount + chargeAmount + operatingCostAmount + otherAmount;

		alert(`Efter skattereduktion:\n\n${cost}kr/mån`);
	};
</script>

<div class="p-6 flex items-start pt-12 justify-center">
	<form
		on:submit|preventDefault|stopPropagation={handleSubmit}
		class="space-y-6 flex-1 max-w-md pb-12"
	>
		<div class="space-y-4">
			<h1 class="font-medium text-3xl">Räkna ut kostnad</h1>
			<p class="text-gray-600">
				Här kan du räkna ut vad det skulle kosta för dig varje månad att bo i en bostadsrätt
				beroende på olika parametrar.
			</p>
		</div>

		<hr />

		<div class="flex flex-col space-y-2">
			<label for="price">Bostadens kostnad</label>
			<input id="price" bind:value={price} type="text" placeholder="3 500 000" />
		</div>

		<div class="flex flex-col space-y-2">
			<label for="charge">Månadsavgit</label>
			<input id="charge" bind:value={charge} type="text" placeholder="1 500" />
		</div>

		<div class="flex flex-col space-y-2">
			<label for="operatingCost">Driftskostnad/år</label>
			<input id="operatingCost" bind:value={operatingCost} type="text" placeholder="4 000" />
		</div>

		<div class="flex flex-col space-y-2">
			<label for="grade">Lånegrad (%)</label>
			<input id="grade" bind:value={grade} type="text" placeholder="85%" />
		</div>

		<div class="flex flex-col space-y-2">
			<label for="interest">Ränta (%)</label>
			<input id="interest" bind:value={interest} type="text" placeholder="1,2%" />
		</div>

		<div class="flex flex-col space-y-2">
			<label for="amortizationRate">Ammorteringsgrad</label>
			<select bind:value={amortizationRate} id="amortizationRate">
				<option value="1">1%</option>
				<option value="2">2%</option>
				<option value="3">3%</option>
			</select>
		</div>

		<div class="flex flex-col space-y-2">
			<label for="other">Övriga månadskostnader</label>
			<input id="other" bind:value={other} type="text" placeholder="" />
		</div>

		<button
			class="bg-emerald-500 text-white border-none w-full p-2 rounded-md text-lg hover:bg-emerald-600 transition"
			type="submit">Räkna ut</button
		>

		<a class="block !mt-24" target="_blank" rel="noopener noreferrer" href="https://albingroen.com">
			<img
				src="https://res.cloudinary.com/albin-groen/image/upload/v1620555918/signature_gy601x.png"
				alt="Albin Groen signature and profile"
				class="w-64 opacity-50 hover:opacity-100 transition"
			/>
		</a>
	</form>
</div>
