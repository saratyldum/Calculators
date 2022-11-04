<template>
	<div class="calculator">
		<div class="calculator__output" placeholder="0"> {{ firstValue || secondValue || 0 }} </div>
		<button @click="clear" class="C operator">C</button>
		<button @click="handleOperatorClicked('%')" class="operator">%</button>
		<button @click="handleOperatorClicked('/')" class="operator">/</button>
		<button @click="handleNumberClicked(7)">7</button>
		<button @click="handleNumberClicked(8)">8</button>
		<button @click="handleNumberClicked(9)">9</button>
		<button @click="handleOperatorClicked('*')" class="operator">x</button>
		<button @click="handleNumberClicked(4)">4</button>
		<button @click="handleNumberClicked(5)">5</button>
		<button @click="handleNumberClicked(6)">6</button>
		<button @click="handleOperatorClicked('-')" class="operator">-</button>
		<button @click="handleNumberClicked(1)">1</button>
		<button @click="handleNumberClicked(2)">2</button>
		<button @click="handleNumberClicked(3)">3</button>
		<button @click="handleOperatorClicked('+'); add" class="operator">+</button>
		<button @click="handleNumberClicked(0)">0</button>
		<button @click="handleNumberClicked('.')">.</button>
		<button @click="handleEqualsInput" class="equal operator">=</button>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				firstValue: '',
				secondValue: '',
				operator: '',
			}
		},

		computed: {
			firstValueAsNumber() {
				return Number(this.firstValue)
			},
		},

		methods: {
			clear() {
				this.firstValue = '';
				this.secondValue = 0;
				this.operator = '';
			},

			calculate() {
				switch(this.operator) {
					case '+':
						this.secondValue += this.firstValueAsNumber;
						break;
					case '-':
						this.secondValue -= this.firstValueAsNumber;
						break;
					case '/':
						this.secondValue /= this.firstValueAsNumber;
						break;
					case '*':
						this.secondValue *= this.firstValueAsNumber;
						break;
					case '%':
						// this.secondValue = Number(this.firstValue) / 100;
					default:
						this.secondValue = this.firstValueAsNumber;
					}
				},

			handleOperatorClicked(operator) {
				this.calculate();
				this.operator = operator;
				this.firstValue = ""
			},

			handleNumberClicked(number) {
				if (number === ('.')) {
					if (!this.firstValue.includes('.')) {
						this.firstValue += number;
					}
				} else {
					this.firstValue += number;
				}
			},

			handleEqualsInput() {
				this.calculate()
				this.firstValue = ''
			},
		}
	}

</script>

<style scoped>
	body {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	button {
		background-color: white;
		border: 1px solid black;
		border-radius: 5px;
		cursor: pointer;
		font-size: 20px;
	}

	button:active {
		filter: brightness(0.9);
	}
	.calculator {
		width: 300px;
		height: 300px;
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 0.5em;
		background-color: #FFDBFB;
		padding: 1em;
		box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.3);
		margin: 3em auto;
	}

	.calculator__output {
		grid-column: 1 / 5;
		border: 1px black solid;
		background-color: white;
		border-radius: 5px;
		height: 2.5em;
		display: flex;
		justify-content: right;
		align-items: center;
		padding-right: 1em;
		font-size: 25px;
		overflow: hidden;
	}

	.C {
		grid-column: 1 / 3;
	}

	.equal {
		grid-column: 3 / 5;
	}

	.operator {
		background-color: #9E55D7;
		color: white;
	}

</style>