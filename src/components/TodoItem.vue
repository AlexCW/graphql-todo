<template>
	<v-list-tile
	@click=""
	>
	{{todo.title}}
	</v-list-tile>
</template>

<script>
export default {
	name: 'todo-item',
	props: {
		todo: {
			type: Object,
			default: null
		}
	}
}
</script>