<template>
	<Calculator/>
	<LengthConverter/>
</template>

<script>
	import Calculator from '../components/Calculator.vue'
	import LengthConverter from '../components/LengthConverter.vue'

	export default {
		components: {
			Calculator,
			LengthConverter
		}
	}
</script>

<style>
	body {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
</style>