<template>

	

	<table class="table">
		<tr>
			<td colspan="2"><h1 class="head">{{ mainHeader }}</h1></td>
		</tr>
		<tr v-for="(task, index) in tasks">
			<td>{{ task.text }}</td>
			<td><button @click="deleteTask(index)"> удалить </button> </td>
		</tr>
		<tr>
			<td><input type="text" v-model="textTask" placeholder="задача"
					@keyup.enter="clickButton('mainButton', textTask)">
			</td>
			<td><button id="mainButton" v-show="textTask != ''" @click="addToArray(), clearInput()">Добавить</button>
			</td>
		</tr>
	</table>


</template>

<script>
export default {
	data() {
		return {
			mainHeader: 'to-do list', //название переменной
			tasks: [],
			textTask: ''
		}
	},
	methods: {
		addToArray() {
			this.tasks.push({
				text: this.textTask
			})

		},
		clearInput() {
			this.textTask = ''
		},
		deleteTask(index) {
			this.tasks.splice(index, 1)
		},
		clickButton(id, text) {
			if (text != '') { document.getElementById(id).click() }
		}
	}
}
</script>

<style scoped>
h1 {
	color: rgb(49, 166, 63);
	font-weight: lighter;
}

.head {
	text-align: center;
}
.table {
	margin:auto;
	
}
button {
	width:100px;
}

</style>
