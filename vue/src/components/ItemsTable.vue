<template>
  <table>
    <thead>
    <tr>
      <th>#</th>
      <th>Title</th>
      <th>Description</th>
      <th>Edit</th>
    </tr>
    </thead>
    <tbody>
    <tr v-if="!items.length">
      <td colspan="4" class="text-center">No data</td>
    </tr>
    <items-table-row v-for="(item, index) in items" :key="item.title" :item="item" :index="index"></items-table-row>
    </tbody>
  </table>
</template>

<script>
import ItemsTableRow from "@/components/ItemsTableRow";
export default {
  name: "ItemsTable",
  components: {ItemsTableRow},
  props: {
    items: {
      type: Array,
    }
  },
}
</script>

<style scoped>

</style>
