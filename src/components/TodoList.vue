<template>
	<v-layout row>
		<v-flex xs12 sm6 offset-sm3>
			<v-card>
				<v-toolbar color="teal" dark>
					<v-toolbar-side-icon></v-toolbar-side-icon>

					<v-toolbar-title>Todo Example</v-toolbar-title>

					<v-spacer></v-spacer>
					<v-btn icon>
							<v-icon @click="addMode = !addMode">add</v-icon>
					</v-btn>
				</v-toolbar>

				<v-list two-line class="lists">
					<v-list-tile
					v-for="todo in tasksToDo"
					:key="todo.title"
					@click=""
					>
					{{todo.title}}
					</v-list-tile>
				</v-list>
			</v-card>
		</v-flex>
	</v-layout>
</template>

<script>
import gql from 'graphql-tag'
export default {
	name: 'todo-list',

	data () {
		return {
			allTodos: []
		}
	},
	apollo: {
		allTodos: {
			query: gql`{ allTodos { id, completed, title } }`
		}
	},
	computed: {
		tasksToDo () {
			return this.allTodos.filter(
				task => !task.completed
			)
		},
	},
}
</script>