<template>
	<form @submit.prevent="FormHandler">
		<input type="text" v-model="desc" placeholder="Description.." />
		<input type="number" v-model="salary" placeholder="Enter Salary.." />
		<input type="date" v-model="date" placeholder="Date..." />
		<input type="submit" value="submit" />
	</form>
</template>

<script>
export default {
	data() {
		return {
			desc: '',
			salary: null,
			date: null,
		};
	},
	methods: {
		FormHandler() {
			let d = this.date.split('-');
			let newD = new Date(d[0], d[1], d[2]);
			const formData = {
				desc: this.desc,
				value: parseInt(this.salary),
				date: newD.getTime(),
				id: Date.now(),
			};
			this.$emit('formData', formData);
			this.desc = '';
			this.salary = null;
			this.date = null;
		},
	},
};
</script>

<style scoped>
form {
	display: flex;
	justify-content: center;
	margin-top: 30px;
}
form input {
	color: #888;
	border: none;
	outline: none;
	font-size: 20px;
}
form input::placeholder {
	color: #aaa;
}
form input:not([type='submit']) {
	display: block;
	background: #fff;
	border: none;
	outline: none;
	padding: 5px 15px;
}
form input[type='submit'] {
	display: block;
	background: none;
	border: none;
	outline: none;
	color: #fff;
	font-weight: 500;
	text-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);
	padding: 5px 15px;
	background-color: #ffce00;
	cursor: pointer;
}
form input:first-of-type {
	border-radius: 8px 0px 0px 8px;
}
form input:last-of-type {
	border-radius: 0px 8px 8px 0px;
}
</style>
