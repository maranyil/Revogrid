<template>
  <div id="app">
    <v-grid
      class="tabla"  
      theme="compact"
      :source="rows"
      :columns="columns"
    ></v-grid>
  </div>
</template>
 
<script>
import VGrid from "@revolist/vue-datagrid";

const columns = [{
  name: 'Person name',
  prop: 'name',

  // use this to return custom html per column
  columnTemplate: (createElement, column) => {
    return createElement('span', {
      style: {
        color: 'red'
      },
    }, column.name);
  },
}];

export default {
  name: "RevoGrid",
  components: {
    VGrid,
  },
  data() {
    return {
      columns: [],
      rows: [{
        name: "1",
        details: "Item 1",
      }],
    };
  },
  created () {
      this.assignCol()
  },
  methods: {
      assignCol() {
          this.columns = columns
      }
  }
};
</script>
<style scoped>
  .tabla {
      height: 900px;
  }
</style>
