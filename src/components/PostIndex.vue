<template>
	<main>
		<div class="container py-4">
			<PostCreate @create-post="createPost"></PostCreate>

			<hr class="my-4" />

			<div class="row g-3">
				<div class="col col-4">
					<PostItem title="제목" contents="내용1"></PostItem>
				</div>
				<div class="col col-4">
					<PostItem
						:title="post.title"
						:contents="post.contents"
						:is-like="post.isLike"
						:type="post.type"
						@toggle-like="post.isLike = !post.isLike"
					></PostItem>
				</div>
				<div v-for="post in posts" :key="post.id" class="col col-4">
					<PostItem
						:title="post.title"
						:contents="post.contents"
						:type="post.type"
						:is-like="post.isLike"
						@toggle-like="post.isLike = !post.isLike"
					></PostItem>
				</div>
			</div>

			<hr class="my-4" />
			<LabelInput v-model="username" label="이름"></LabelInput>
		</div>
	</main>
</template>

<script>
import { ref, reactive } from 'vue';
import PostItem from '@/components/PostItem.vue';
import PostCreate from '@/components/PostCreate.vue';
import LabelInput from '@/components/LabelInput.vue';
import LabelTitle from '@/components/LabelTitle.vue';
import Username from '@/components/Username.vue';

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
		const firstname = ref('');
		const lastname = ref('');
		return { post, posts, createPost, username, firstname, lastname };
	},
	components: { PostItem, PostCreate, LabelInput, LabelTitle, Username },
};
</script>

<style lang="scss" scoped></style>
