<template>
	<div></div>
</template>

<script>
import { reactive, ref, watch } from 'vue';
export default {
	setup() {
		const x = ref(0);
		const y = ref(0);
		const obj = reactive({
			count: 0,
		});

		// watch(
		// 	() => x.value + y.value,
		// 	(sum, oldValue) => {
		// 		console.log('sum : ', sum);
		// 		console.log('oldValue : ', oldValue);
		// 	},
		// );
		// watch([x, y], ([newX, newY]) => {
		// 	console.log(newX, newY);
		// });

		// watch(obj, (newValue, oldValue) => {
		// 	console.log('newValue :', newValue);
		// 	console.log('oldValue :', oldValue);
		// });
		console.log(typeof obj.count);
		watch(
			() => obj.count,
			(newValue, oldValue) => {
				console.log('newValue :', newValue);
				console.log('oldValue :', oldValue);
			},
		);

		return { x, y, obj };
	},
};
</script>

<style lang="scss" scoped></style>
