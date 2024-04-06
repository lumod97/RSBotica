<template>
  <table class="table tablesorter" :class="tableClass">
    <thead :class="theadClasses">
      <tr>
        <slot name="columns">
          <th v-for="(column, index) in columns" :key="index">{{ column.label }}</th>
        </slot>
      </tr>
    </thead>
    <tbody :class="tbodyClasses">
      <tr v-for="(item, index) in data" :key="index">
        <!-- <slot :row="item"> -->
          <template v-for="(column, index) in columns">
            <td :key="index" v-if="hasValue(item, column)" >
              <slot :name="column.key" :item="item"> {{ itemValue(item, column) }} </slot>
            </td>
          </template>
        <!-- </slot> -->
      </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  name: "base-table",
  props: {
    columns: {
      type: Array,
      default: () => [],
      description: "Table columns",
    },
    data: {
      type: Array,
      default: () => [],
      description: "Table data",
    },
    type: {
      type: String, // striped | hover
      default: "",
      description: "Whether table is striped or hover type",
    },
    theadClasses: {
      type: String,
      default: "",
      description: "<thead> css classes",
    },
    tbodyClasses: {
      type: String,
      default: "",
      description: "<tbody> css classes",
    },
  },
  computed: {
    tableClass() {
      return this.type && `table-${this.type}`;
    },
  },
  methods: {
    hasValue(item, column) {
      return item[0] !== "undefined";
    },
    itemValue(item, column) {
      return item[column.key];
    },
  },
};
</script>
<style></style>
