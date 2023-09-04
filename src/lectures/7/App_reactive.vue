<template>
	<button v-on:click="increment">Click {{ state.count }}</button>
	<button v-on:click="increment">Deep Click {{ state.deep.count }}</button>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		const state = reactive({
			count: 0,
			deep: {
				count: 0,
			},
		});
		const increment = () => {
			state.count++;
			state.deep.count++;
		};
		return {
			state,
			increment,
		};
	},
};
</script>

<style lang="scss" scoped></style>
