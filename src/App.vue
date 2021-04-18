<template>
	<Header :totalIncome="totalIncome" /><Form
		@formData="addIncome"
	/><income-list :incomes="income" @deleted="deleted" />
</template>

<script>
import Header from './components/Header';
import Form from './components/Form';
import IncomeList from './components/IncomeList';

export default {
	name: 'App',
	data() {
		return {
			income: [],
		};
	},
	computed: {
		totalIncome() {
			var temp = 0;
			if (this.income.length > 0) {
				for (let i = 0; i < this.income.length; i++) {
					temp += this.income[i].value;
				}
			}
			return temp;
		},
	},
	methods: {
		addIncome(data) {
			this.income.push(data);
		},
		deleted(id) {
			if (confirm('Are you sure to delete this task?')) {
				this.income = this.income.filter((task) => task.id !== id);
			}
		},
	},
	components: {
		Header,
		Form,
		IncomeList,
	},
	emits: ['formData', 'deleted'],
};
</script>

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-family: 'Fira Sans', sans-serif;
}
body {
	background: #eee;
}
</style>
