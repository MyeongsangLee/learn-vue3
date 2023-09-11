<template>
	<main>
		<div class="container py-4">
			<PostCreate @create-post="createPost"></PostCreate>

			<hr class="my-4" />

			<div class="row g-3">
				<div class="col col-4">
					<AppCard title="제목" contents="내용1"></AppCard>
				</div>
				<div class="col col-4">
					<AppCard
						:title="post.title"
						:contents="post.contents"
						:is-like="post.isLike"
						:type="post.type"
						@toggle-like="post.isLike = !post.isLike"
					></AppCard>
				</div>
				<div v-for="post in posts" :key="post.id" class="col col-4">
					<AppCard
						:title="post.title"
						:contents="post.contents"
						:type="post.type"
						:is-like="post.isLike"
						@toggle-like="post.isLike = !post.isLike"
					></AppCard>
				</div>
			</div>

			<hr class="my-4" />
			<LabelInput
				:model-value="username"
				@update:model-value="value => (username = value)"
			></LabelInput>
		</div>
	</main>
</template>

<script>
import { ref, reactive } from 'vue';
import AppCard from '@/components/AppCard.vue';
import PostCreate from '@/components/PostCreate.vue';
import LabelInput from '@/components/LabelInput.vue';

export default {
	setup() {
		const post = reactive({
			title: '제목2',
			contents: '내용2',
			isLike: true,
			type: 'news',
		});

		const posts = reactive([
			{ id: 3, title: '제목3', contents: '내용3', isLike: true, type: 'news' },
			{ id: 4, title: '제목4', contents: '내용4', isLike: true, type: 'news' },
			{ id: 5, title: '제목5', contents: '내용5', isLike: false, type: 'n' },
			{ id: 6, title: '제목6', contents: '내용6', isLike: false, type: '' },
		]);

		const createPost = newPost => {
			console.log('createPost');
			console.log('newTitle : ', newPost);
			posts.push(newPost);
		};

		const username = ref('');
		return { post, posts, createPost, username };
	},
	components: { AppCard, PostCreate, LabelInput },
};
</script>

<style lang="scss" scoped></style>
