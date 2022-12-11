<template>
	<div id="calc-overall">
		<h1> Simple Calculator </h1>
		<input v-model="calcInput" type="text" id="calcInput" name="calcInput" />
		<simple-button
			@add-number="numberAdd"
			@subtract-number="numberSubtract"
			@multiply-number="numberMultiply"
			@divide-number="numberDivide"
			@equals-number="numberEquals"
		></simple-button>
	</div>
</template>

<script>
import SimpleButton from './SimpleButton.vue';

export default {
	data() {
		return {
			equation: 0,
			number1: 0,
			number2: 0,
			operator: '',
			calcInput: 0,
		};
	},
	components: { SimpleButton },
	methods: {
		numberAdd(numAdd) {
			this.number1 = parseInt(this.calcInput);
			this.operator = numAdd;
		},
		numberSubtract(numSub) {
			this.number1 = parseInt(this.calcInput);
			this.operator = numSub;
		},
		numberMultiply(numMul) {
			this.number1 = parseInt(this.calcInput);
			this.operator = numMul;
		},
		numberDivide(numDiv) {
			this.number1 = parseInt(this.calcInput);
			this.operator = numDiv;
		},
		numberEquals() {
			this.number2 = this.calcInput;
			switch (this.operator) {
				case '+':
					this.equation = parseInt(this.number1) + parseInt(this.number2);
					break;
				case '-':
					this.equation = parseInt(this.number1) - parseInt(this.number2);
					break;
				case '*':
					this.equation = parseInt(this.number1) * parseInt(this.number2);
					break;
				case '/':
					this.equation = parseInt(this.number1) / parseInt(this.number2);
					break;

				default:
					break;
			}
			console.log(this.equation);
			this.calcInput = this.equation;
		},
	},
};
</script>
