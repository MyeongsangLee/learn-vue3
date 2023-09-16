<template>
	<main>
		<div class="container py-4">
			<MyButton
				class="my-button"
				id="my-button"
				v-on:click="sayHello"
			></MyButton>
			<LabelInput label="이름"></LabelInput>
			<hr />

			<FancyButton>Click!!!!!<span style="color: red">@@@@</span></FancyButton>
			<!-- <FancyButton v-slot="{ fancyMessage }">{{ fancyMessage }}</FancyButton> -->
			<FancyButton>
				<template v-slot="{ fancyMessage }">{{ fancyMessage }}></template>
			</FancyButton>
			<hr />
			<AppCard>
				<!-- <template v-slot:header>제목</template> -->
				<template v-slot:[slotArgs]>제목</template>
				<template #default="{ childMessage, helloMessage }">
					디폴트입니다. {{ message }}
					{{ childMessage }}
					<br />
					{{ helloMessage }}
				</template>
				<!-- 암시적으로 디폴트 슬롯 입니다. -->
				<!-- <template #footer>푸터</template> -->
			</AppCard>
			<hr />
			<AppCard>게시글입니다.</AppCard>
		</div>
	</main>
</template>

<script>
import { ref } from 'vue';
import MyButton from './MyButton.vue';
import LabelInput from './LabelInput.vue';
import FancyButton from './FancyButton.vue';
import AppCard from './AppCard.vue';
export default {
	components: { MyButton, LabelInput, FancyButton, AppCard },
	setup() {
		const slotArgs = ref('header');
		const sayHello = () => {
			alert('안녕하세요!!');
		};
		return { sayHello, slotArgs };
	},
};
</script>

<style lang="scss" scoped></style>
