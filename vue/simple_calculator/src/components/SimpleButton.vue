<template>
	<div id="buttons">
		<div id="button-upper-row">
			<button id="button-up" @click="add"> {{ addNum }} </button>
			<button id="button-up" @click="subtract"> {{ subNum }} </button>
			<button id="button-up" @click="multiply"> {{ mulNum }} </button>
			<button id="button-up" @click="divide"> {{ divNum }} </button>
		</div>
		<button id="button-down" @click="equals"> {{ equNum }} </button>
	</div>
</template>

<script>
export default {
	emits: [
		'add-number' -
			'subtract-number' -
			'multiply-number' -
			'divide-number' -
			'equals-number',
	],
	data() {
		return {
			addNum: '+',
			subNum: '-',
			mulNum: '*',
			divNum: '/',
			equNum: '=',
		};
	},
	methods: {
		add() {
			this.$emit('add-number', this.addNum);
		},
		subtract() {
			this.$emit('subtract-number', this.subNum);
		},
		multiply() {
			this.$emit('multiply-number', this.mulNum);
		},
		divide() {
			this.$emit('divide-number', this.divNum);
		},
		equals() {
			this.$emit('equals-number', this.equNum);
		},
	},
};
</script>
