<template>
  <v-data-table
		:headers="columnNames"
		:items="tableRows"/>
</template>

<script>
export default {
	props: {
		columnNames: {
			type: Array,
			required: true,
		},
		tableRows: {
			type: Array,
			required: true,
		},
	},
};
</script>

<style>

</style>