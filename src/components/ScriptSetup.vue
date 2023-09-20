<template>
	<div>
		{{ msg }}
		<br />
		{{ message }}
		<input v-model="message" type="text" />
		<button v-on:click="sayHello">Click</button>
		<PostItem type="news" title="제목" contents="내용" isLike="true"></PostItem>
		<hr />
		<TemplateRefsChild ref="child"></TemplateRefsChild>
		<template v-if="child">{{ child.message }}</template>
	</div>
</template>

<script setup>
import { ref } from 'vue';
import PostItem from '@/components/setup/PostItem.vue';
import TemplateRefsChild from '@/components/setup/TemplateRefsChild.vue';
import axios from 'axios';

const msg = 'Hello World~!!';
const message = ref('');
const sayHello = () => {
	alert('Hello world~!');
};
const child = ref(null);

defineExpose({
	msg,
});

const response = await axios(
	'https://dummy.restapiexample.com/api/v1/employees',
);
console.log('response:', response);
</script>

<style lang="scss" scoped></style>
