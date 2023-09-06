<template>
	<div>
		<h2>input value</h2>
		<!-- <input type="text" :value="inputValue"/> -->
		<!-- <input
			type="text"
			:value="inputValue"
			@input="event => (inputValue = event.target.value)"
		/> -->
		<input type="text" v-model="inputValue" />
		<div>{{ inputValue }}</div>

		<h2>textarea value</h2>
		<!-- <textarea :value="textareaValue"></textarea> -->
		<!-- <textarea
			:value="textareaValue"
			@input="event => (textareaValue = event.target.value)"
		></textarea> -->
		<textarea v-model="textareaValue"></textarea>
		<div>{{ textareaValue }}</div>

		<h2>checkbox value</h2>
		<label for="checkbox">{{ checkboxValue }}</label>
		<!-- <input type="checkbox" id="checkbox" :checked="checkboxValue" /> -->
		<!-- <input
			type="checkbox"
			id="checkbox"
			@change="event => (checkboxValue = event.target.checked)"
		/> -->
		<!-- <input type="checkbox" id="checkbox" @change="addCheckbox" /> -->
		<!-- <input type="checkbox" id="checkbox" v-model="checkboxValue" /> -->
		<input
			type="checkbox"
			id="checkbox"
			v-model="checkboxValue"
			true-value="Yes"
			false-value="No"
		/>

		<h2>checkbox values</h2>
		<label>
			<input type="checkbox" value="html" v-model="checkboxValues" />
			HTML
		</label>
		<label>
			<input type="checkbox" value="css" v-model="checkboxValues" />
			CSS
		</label>
		<label>
			<input type="checkbox" value="javascript" v-model="checkboxValues" />
			JavaScript
		</label>
		<div>{{ checkboxValues }}</div>

		<h2>radio value</h2>
		<!-- <label>
			<input type="radio" name="type" value="O" :checked="radioValue === 'O'" />
			O형
		</label>
		<label>
			<input type="radio" name="type" value="A" :checked="radioValue === 'A'" />
			A형
		</label> -->
		<!-- <label>
			<input
				type="radio"
				name="type"
				value="O"
				:checked="radioValue === 'O'"
				@change="event => (radioValue = event.target.value)"
			/>
			O형
		</label>
		<label>
			<input
				type="radio"
				name="type"
				value="A"
				:checked="radioValue === 'A'"
				@change="event => (radioValue = event.target.value)"
			/>
			A형
		</label> -->
		<label>
			<input type="radio" name="type" value="O" v-model="radioValue" />
			O형
		</label>
		<label>
			<input type="radio" name="type" value="A" v-model="radioValue" />
			A형
		</label>
		<div>{{ radioValue }}</div>

		<h2>select value</h2>
		<!-- <select :value="selectedValue"> -->
		<!-- <select
				:value="selectedValue"
				@change="event => (selectedValue = event.target.value)" -->
		<select v-model="selectedValue">
			<option value="html">HTML 수업</option>
			<option value="css">CSS 수업</option>
			<option value="javascript">JavaScript 수업</option>
		</select>
		<div>{{ selectedValue }}</div>
	</div>
</template>

<script>
import { ref } from 'vue';
export default {
	setup() {
		const inputValue = ref('');
		const textareaValue = ref('');
		const checkboxValue = ref('No');
		const checkboxValues = ref([]);
		const radioValue = ref('O');
		const selectedValue = ref('html');
		// const addCheckbox = event => (checkboxValue.value = event.target.checked);

		return {
			inputValue,
			textareaValue,
			checkboxValue,
			checkboxValues,
			radioValue,
			selectedValue,
			// addCheckbox,
		};
	},
};
</script>

<style lang="scss" scoped></style>
