<template>
	<h1>Vue app</h1>
	<form @submit.prevent="addTask()">
		<label>Add text for </label>
		<input
			v-model="newTask"
		>
		<button>Add task</button>
	</form>
	<h2>Tasks</h2>
	<ul>
		<li
			v-for="(task, index) in tasks"
		>
			<span>{{ task.content }}</span>
			<button @click="removeTask(index)">Remove</button>
		</li>
	</ul>
	<h4 v-if="tasks.length === 0">Empty list.</h4>

	<h2>Counter</h2>
	
  <button @click="count--">-</button>

	{{ count }}
	
  <button @click="count++">+</button>
	
</template>

<script setup>
	import { ref } from 'vue';
		
			const newTask = ref('');

			const defaultData = [{
				content: ''
			}]

			const count = ref(0)

			const tasks = ref(defaultData);
			
			function addTask () {
				if (newTask.value) {
					tasks.value.push({
						content: newTask.value
					});
					newTask.value = '';
				}
			}

			function removeTask (index) {
				tasks.value.splice(index, 1);
			}

</script>

<style lang="scss">
body {
	margin: 0;
	padding: 0;
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	background-color: rgb(106, 70, 70);
	color: white;
	#app {
		max-width: 600px;
		margin-left: auto;
		margin-right: auto;
		padding: 20px;
		h1 {
			font-weight: bold;
			font-size: 28px;
			text-align: center;
		}
		form {
			display: flex;
			flex-direction: column;
			width: 100%;
			label {
				font-size: 24px;
				font-weight: bold;
			}
			input,
			button {
				height: 48px;
				box-shadow: none;
				outline: none;
				padding-left: 12px;
				padding-right: 12px;
				font-size: 18px;
				margin-bottom: 12px;
				border-radius: 15px;
			}
			input {
				background-color: transparent;
				color: inherit;
			}
		}
		button {
			cursor: pointer;
			background-color: rgb(230, 230, 230);
			border: 1px solid grey;
			color: #1f2023;
			font-weight: bold;
			outline: none;
			border-radius: 5px;

		}
		h2 {
			font-size: 22px;
		}
		ul {
			padding: 10px;
			li {
				display: flex;
				justify-content: space-between;
				align-items: center;
				border: 2px solid white;
				padding: 12px;
				margin-bottom: 12px;
				font-size: 24px;				
				span {
					cursor: pointer;
				}
				button {
					font-size: 18px;
				}
			}
		}
		h4 {
			text-align: center;
			opacity: 0.5;
			margin: 0;
		}
	}
}
</style>
