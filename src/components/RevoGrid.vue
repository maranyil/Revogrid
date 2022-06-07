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

export default {
  name: "RevoGrid",
  components: {
    VGrid,
  },
  data() {
    return {
      columns: [],
      rows: [
        {
          name: "Juan",
          details: "Item 1",
        },
      ],
    };
  },
  created() {
    this.assignCol();
  },
  methods: {
    assignCol() {
      const heads = [
        { name: 'Persona', prop: "name" },
        { name: 'Edad', prop: "age" },
        { name: 'Bici', prop: "bike" },
      ]
      const props = heads.map(el => el.prop)
      console.log(props)
      const columns = [
        {
          name: heads.map(el => el.name),
          prop: 'name',


          // use this to return custom html per column
          columnTemplate: (createElement, column) => {
            return createElement(
              "span",
              {
                style: {
                  color: "red",
                },
              },
              column.name
            );
          },
        },
      ];
      this.columns = columns;
    },
  },
};
</script>
<style scoped>
.tabla {
  height: 900px;
}
</style>
