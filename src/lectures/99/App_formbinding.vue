<template>
	<div>
		<p>메세지: {{ message }}</p>
		<input v-model="message" placeholder="메세지 입력하기" />
		<div></div>
		<button v-on:click="addInputEvent">input</button>

		<span>여러 줄 메세지:</span>
		<p style="white-space: pre-line">{{ textmessage }}</p>
		<textarea
			v-model="textmessage"
			placeholder="여러 줄을 추가해보세요"
		></textarea>
		<div></div>
		<button v-on:click="addTextareaEvent">textarea</button>

		<div>체크된 이름: {{ checkedNames }}</div>

		<input type="checkbox" id="jack" value="젝" v-model="checkedNames" />
		<label for="jack">젝</label>

		<input type="checkbox" id="john" value="존" v-model="checkedNames" />
		<label for="john">존</label>

		<input type="checkbox" id="mike" value="마이크" v-model="checkedNames" />
		<label for="mike">마이크</label>
		<div></div>
		<button v-on:click="addCheckboxEvent">checkbox</button>

		<div>선택한 것: {{ picked }}</div>

		<input type="radio" id="one" value="하나" v-model="radioPicked" />
		<label for="one">하나</label>

		<input type="radio" id="two" value="둘" v-model="radioPicked" />
		<label for="two">둘</label>
		<div></div>
		<button v-on:click="addRadiobuttonEvent">radio</button>

		<div>선택됨: {{ selected }}</div>

		<select v-model="selected">
			<option disabled value="">다음 중 하나를 선택하세요</option>
			<option>가</option>
			<option>나</option>
			<option>다</option>
		</select>
		<div></div>
		<button v-on:click="addSelectedEvent">radio</button>
	</div>
</template>

<script>
import { reactive, ref } from 'vue';
export default {
	setup() {
		const aaa = reactive(); //array, object {}
		const message = ref('');
		const textmessage = ref('');
		const checkedNames = ref([]);
		const radioPicked = ref('');
		const selected = ref('');

		const addInputEvent = () => {
			console.log(message.value);
		};
		const addTextareaEvent = () => {
			console.log(textmessage.value);
		};
		const addCheckboxEvent = () => {
			// console.log(checkedNames.value);
			for (var value of checkedNames.value) {
				console.log(value);
			}
		};
		const addRadiobuttonEvent = () => {
			console.log(radioPicked.value);
		};
		const addSelectedEvent = () => {
			console.log(selected.value);
		};

		return {
			aaa,
			message,
			textmessage,
			checkedNames,
			radioPicked,
			selected,
			addInputEvent,
			addTextareaEvent,
			addCheckboxEvent,
			addRadiobuttonEvent,
			addSelectedEvent,
		};
	},
};
</script>

<style lang="scss" scoped></style>
