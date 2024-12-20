<template>
	<div class="container column">
		<Form @emitAdd="add"></Form>
		<UserInfo :elements="elements"></UserInfo>
	</div>
	<div class="container">
		<Comments :loadComments="loadComments" :deleteComments="deleteComments" :comments="comments" :isLoading="isLoading">
		</Comments>
	</div>
</template>

<script>
import Form from "./components/Form.vue";
import UserInfo from "./components/UserInfo.vue";
import Comments from "./components/Comments.vue";
export default {
	data() {
		return {
			elements: [],
			comments: [],
			isLoading: false,
		};
	},
	methods: {
		add({ type, value }) {
			console.log(this.elements)
			this.elements.push({
				type,
				value,
				id: Math.random() * 10000,
			});
		},
		async loadComments() {
			this.isLoading = true;
			const response = await fetch(
				"https://jsonplaceholder.typicode.com/comments?_limit=42"
			);
			if (response.ok) {
				this.isLoading = false;
				this.comments = await response.json();
			}
		},
		deleteComments() {
			this.comments = [];
		},
	},
	components: { Form, UserInfo, Comments },
};
</script>

<style>
.avatar {
	display: flex;
	justify-content: center;
}

.avatar img {
	width: 150px;
	height: auto;
	border-radius: 50%;
}
</style>
