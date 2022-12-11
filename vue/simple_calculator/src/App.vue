<template>
	<the-calculator> </the-calculator>
</template>

<script>
import TheCalculator from './components/TheCalculator.vue';

export default {
	name: 'App',
	components: {
		TheCalculator,
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #6600ff;
	margin-top: 60px;
}

body {
	background-color: rgba(16, 17, 17, 0.449);
}
#calc-overall {
	display: block;
	margin-left: auto;
	margin-right: auto;
	width: 500;
	display: flex;
	align-items: center;
	justify-content: center;
	flex-direction: column;
}

#button-upper-row {
	display: flex;
	justify-content: space-evenly;
	flex-direction: row;
}

#button-up {
	margin-top: 20px;
	width: 100px;
	height: 35px;
	display: inline-block;
	outline: 0;
	border: none;
	cursor: pointer;
	font-weight: 600;
	border-radius: 4px;
	font-size: 13px;
	height: 30px;
	background-color: #9147ff;
	color: white;
	padding: 0 20px;
}
#button-down {
	margin-top: 20px;
	width: 500px;
	height: 35px;
	display: inline-block;
	outline: 0;
	border: none;
	cursor: pointer;
	font-weight: 600;
	border-radius: 4px;
	font-size: 13px;
	height: 30px;
	background-color: #9147ff;
	color: white;
	padding: 0 20px;
}

#calcInput {
	color: rgba(0, 0, 0, 0.87);
	border-bottom-color: rgba(0, 0, 0, 0.42);
	font-size: 1rem;
	font-weight: 400;
	letter-spacing: 0.009375em;
	text-decoration: inherit;
	text-transform: inherit;
	width: 500px;
	transition: opacity 150ms cubic-bezier(0.4, 0, 0.2, 1);
	border: none;
	border-bottom: 1px solid;
	border-radius: 4px 4px 0 0;
	background: rgb(245, 245, 245);
	height: 56px;
}
</style>
