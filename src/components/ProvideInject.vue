<template>
	<div class="container py-4">
		<div class="card">
			<div class="card-header">ProvideInject Component</div>
			<div class="card-body">
				<button @click="count++">Click</button>
				<p>appMessage: {{ appMessage }}</p>
				<Child></Child>
			</div>
		</div>
	</div>
</template>

<script>
import { inject, provide, readonly, ref } from 'vue';
import Child from './Child.vue';
export default {
	components: { Child },
	setup() {
		const staticMessage = 'static message';
		const message = ref('message');
		const updateMessage = appendMessage => {
			message.value += appendMessage;
		};
		const count = ref(10);

		// provide('static-message', staticMessage);
		// provide('message', { message, updateMessage });
		provide('message', { message: readonly(message), updateMessage });
		provide('count', count);
		console.log('this', this);
		const msg = inject('msg');
		console.log('msg', msg);

		const appMessage = inject('app-message');

		return { staticMessage, message, count, updateMessage, appMessage };
	},
	mounted() {
		console.log('this.msg', this.msg);
	},
};
</script>

<style lang="scss" scoped></style>
