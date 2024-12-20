<template>
	<p>
		<button @click="loadComments" class="btn primary">
			Загрузить комментарии
		</button>
		<button @click="deleteComments" class="btn danger">
			Скрыть комментарии
		</button>
	</p>
	<div class="card">
		<h2>Комментарии</h2>
		<ul class="list">
			<li v-for="comm in comments" :key="comm.id" class="list-item">
				<div>
					<p>
						<strong>{{ comm.email }}</strong>
					</p>
					<small>{{ comm.body }}</small>
				</div>
			</li>
		</ul>
	</div>
	<div v-if="isLoading" class="loader"></div>
</template>

<script>
export default {
	props: {
		isLoading: Boolean,
		comments: Array,
		loadComments: Function,
		deleteComments: Function,
	},
};
</script>

<style lang="scss" scoped></style>
