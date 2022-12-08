<template>
	<div class="converter">
		<h1>Lengdekonverterer</h1>

		<div class="converter__inner">
			<div class="flex">
				<input type="text" placeholder="Input" v-model="input">

				<select class="inputType" v-model="inputType">
					<option value="meter" id="inputMeter">Meter</option>
					<option value="kilometer" id="inputKilometer">Kilometer</option>
					<option value="centimeter" id="inputCentimeter">Centimeter</option>
					<option value="milimeter" id="inputMilimeter">Milimeter</option>
				</select>
			</div>
	
			<span>=</span>
			
			<div class="converter__results">
				<div class="converter__results--meter"> {{ inMeters }}</div>
				<div class="converter__results--kilometer"> {{ inKilometers }}</div>
				<div class="converter__results--centimeter"> {{ inCentimeters }}</div>
				<div class="converter__results--milimeter"> {{ inMilimeters }}</div>
			</div>
		</div>

	</div>
</template>

<script>
	export default {
		data() {
			return {
				input: 0,
				inputType: "meter"
			}
		},

		computed: {
			inKilometers() {
				if (this.inputType === "meter") {
					return `${this.input / 1000} Kilometer`;
				}else if (this.inputType === "kilometer") {
					return `${this.input} Kilometer`;
				}else if (this.inputType === "centimeter") {
					return `${this.input / 100000} Kilometer`;
				}else if (this.inputType === "milimeter") {
					return `${this.input / 1000000} Kilometer`;
				}
			},

			inMeters() {
				if (this.inputType === "meter") {
					return `${this.input} Meter`;
				}else if (this.inputType === "kilometer") {
					return `${this.input * 1000} Meter`;
				}else if (this.inputType === "centimeter") {
					return `${this.input / 100} Meter`;
				}else if (this.inputType === "milimeter") {
					return `${this.input / 1000} Meter`;
				}
			},

			inCentimeters() {
				if (this.inputType === "meter") {
					return `${this.input * 100} Centimeter`;
				}else if (this.inputType === "kilometer") {
					return `${this.input * 100000} Centimeter`;
				}else if (this.inputType === "centimeter") {
					return `${this.input} Centimeter`;
				}else if (this.inputType === "milimeter") {
					return `${this.input / 10} Centimeter`;
				}
			},

			inMilimeters() {
				if (this.inputType === "meter") {
					return `${this.input * 1000} Milimeter`;
				}else if (this.inputType === "kilometer") {
					return `${this.input * 1000000} Milimeter`;
				}else if (this.inputType === "centimeter") {
					return `${this.input * 10} Milimeter`;
				}else if (this.inputType === "milimeter") {
					return `${this.input} Milimeter`;
				}
			},
		}
	}

</script>


<style scoped>
	body {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		font-size: 16px;
	}

	h1 {
		display: block;
		text-decoration: underline;
	}

	input {
		padding: 1em;
		margin-bottom: 2px;
		border: 1px solid gray;
		font-size: 14px;
	}

	select {
		padding: 1em;
		width: 100%;
	}

	span {
		margin: 0em 2em;
		font-size: 1.5em;
		display: flex;
		align-self: center;
	}
	.converter {
		width: 500px;
		background-color: #B7D3FE;
		padding: 2em;
		margin: 5em auto 5em;
		text-align: center;
		display: flex;
		flex-direction: column;
		border-radius: 5px;
		box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
	}

	.converter__inner {
		display: flex;
		padding: 1em;
		justify-content: center;
	}
	.flex {
		display: flex;
		flex-direction: column;
		width: 100%;
		justify-content: center;
	}

	.converter__results--meter, 
	.converter__results--kilometer,
	.converter__results--centimeter,
	.converter__results--milimeter {
		background-color: white;
		border: 1px solid gray;
		padding: 1em;
		margin-bottom: 2px;
		font-size: 14px;
		width: 150px;
	}
</style>