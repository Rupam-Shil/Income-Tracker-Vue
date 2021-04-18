<template>
	<div class="income-list">
		<IncomeItem
			v-for="income in incomes"
			:key="income.id"
			:income="income"
			@deleted="deleted"
		/>
	</div>
</template>

<script>
import IncomeItem from './IncomeItem';
export default {
	components: { IncomeItem },
	props: ['incomes'],
	emits: ['delete'],
	methods: {
		deleted(id) {
			this.$emit('deleted', id);
		},
	},
};
</script>

<style scoped>
.income-list {
	margin-top: 30px;
	padding: 15px;
}
</style>
