<template>
	<div class="layout">
		<group-table v-for="item in items" :key="item.id" :group="item" />
	</div>
</template>

<script>
	import GroupTable from "./group-table.vue";
	import mixin from "@directus/extension-toolkit/mixins/layout";

	export default {
		mixins: [mixin],
		components: {
			GroupTable
		}
	};
</script>

<style lang="scss" scoped>
.layout {
	margin-top: var(--page-padding-top-table);
	padding: 0 var(--page-padding);
}
</style>
