<template>
  <tr>
    <td>{{ index + 1 }}</td>
    <td>
      <template v-if="editable">
        <input class="input-block" type="text" v-model="editableForm.title">
      </template>
      <template v-else>
        {{ item.title }}
      </template>
    </td>
    <td>
      <template v-if="editable">
        <input class="input-block" type="text" v-model="editableForm.description">
      </template>
      <small v-else>{{ item.description }}</small></td>
    <td>
      <button class="btn-danger btn-small" @click="removeItem(item.title)">Delete</button>&nbsp;&nbsp;
      <button class="btn-secondary btn-small" @click="editable = !editable">{{ editable ? 'Cancel' : 'Edit'}}</button>&nbsp;
      <button v-if="editable" class="btn-success btn-small" @click="editItem">Save</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "ItemsTableRow",
  props: {
    item: {
      type: Object,
    },
    index: {
      type: Number,
    },
  },
  data() {
    return {
      editable: false,
      editableForm: null,
    }
  },
  methods: {
    removeItem(title) {
      this.$store.dispatch('DELETE_ITEM', title);
    },
    editItem() {
      this.$store.dispatch('EDIT_ITEM', { editableForm: this.editableForm, index: this.index } );
      this.editable = false;
    }
  },
  watch: {
    editable(value) {
      if (value) {
        this.editableForm = {...this.item};
      } else {
        this.editableForm = null;
      }
    }
  },
}
</script>

<style scoped>

</style>
