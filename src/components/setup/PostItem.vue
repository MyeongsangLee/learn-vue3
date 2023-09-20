<template>
	<div class="card">
		<div class="card-body">
			<!-- <span class="badge bg-secondary">{{
				type === 'news' ? '뉴스' : '공지사항'
			}}</span> -->
			<span class="badge bg-secondary">{{ typeName }}</span>
			<h5 class="card-title mt-2">{{ title }}</h5>
			<p class="card-text">{{ contents }}</p>
			<!-- <a v-if="isLike" href="#" class="btn btn-danger">좋아요</a> -->
			<!-- <a v-else href="#" class="btn btn-outline-danger">좋아요</a> -->
			<a href="#" class="btn" :class="isLikeClass">좋아요</a>
		</div>
	</div>
</template>

<script setup>
import { computed } from 'vue';
const props = defineProps({
	type: {
		type: String,
		default: 'news',
		validator: value => {
			return ['news', 'notice'].includes(value);
		},
	},
	title: {
		type: String,
		required: true,
	},
	contents: {
		type: String,
		// required: true,
	},
	isLike: {
		type: Boolean,
		default: false,
	},
});

const emit = defineEmits(['toggleLike']);

const isLikeClass = computed(() =>
	props.isLike ? 'btn-danger' : 'btn-outline-danger',
);

const typeName = computed(() => (props.type === 'news' ? '뉴스' : '공지사항'));
const toggleLike = () => {
	emit('toggleLike');
};
</script>

<style lang="scss" scoped></style>
