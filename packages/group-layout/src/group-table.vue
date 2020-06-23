<template>
	<div>
		{{ items }}
		<v-table ref="table" :items="items" :columns="columns"></v-table>
	</div>
</template>

<script>
	import mixin from "@directus/extension-toolkit/mixins/layout";

	export default {
		props: ["group"],
		data() {
			return {
				data: null
			};
		},
		async mounted() {
			const collectionItems = await Promise.all(
				this.collections.map(collection => this.$api.getItems(collection))
			);
			this.data = collectionItems;
		},
		computed: {
			id() {
				return this.group.id;
			},
			name() {
				return this.group.group;
			},
			collections() {
				return this.group.collections.filter(Boolean);
			},
			columns() {
				let columns = [];
				if (this.data) {
					this.data.forEach(dataSet => {
						if (dataSet.data.length) {
							columns = [...columns, ...Object.keys(dataSet.data[0])];
						}
					});
				}
				columns = [
					"group_id",
					"group_name",
					"collection_name",
					"collection_position",
					...columns
				];
				// unique values
				columns = [...new Set(columns)];
				return columns.map(column => {
					return { field: column, name: column };
				});
			},
			items() {
				let items = [];
				if (this.data) {
					this.data.forEach((dataSet, index) => {
						dataSet.data.forEach(row => {
							row.group_id = this.id;
							row.group_name = this.name;
							row.collection_name = this.collections[index];
							row.collection_position = index;
							items = [...items, row];
						});
					});
				}
				return items;
			}
		}
	};
</script>
