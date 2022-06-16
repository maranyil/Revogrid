<template>
  <div class="tile">
    <component
      v-if="vGrid"
      :is="vGrid"
      class="grid-container"
      :source="source"
      :columns="columns"
      :pinnedTopRows="pinnedTopRows"
      :pinnedBottomRows="pinnedBottomRows"
      theme="material"
      resize="true"
      range="true"
      rowClass="highlighted"
      @afteredit="afterEdit"
    />
  </div>
</template>

<script>
import generateFakeDataObject from "./dataGenerate";
export default {
  name: "demo-initial",
  data() {
    return {
      vGrid: null,
      source: [],
      pinnedBottomRows: [],
      columns: [],
      pinnedTopRows: [],
    };
  },
  mounted() {
    import('./peopleSample.js').then((e) => {
      const people = e.default;
      const newData = generateFakeDataObject(people, 10);
      for (let key in newData) {
        this[key] = newData[key];
      }
    });
    import('@revolist/vue-datagrid').then((m) => {
      const types = {};
      Promise.all([
        import('@revolist/revogrid-column-select').then((p) => (types['select'] = new p.default())),
        import('@revolist/revogrid-column-date').then((p) => (types['date'] = new p.default())),
        import('@revolist/revogrid-column-numeral').then((p) => (types['number'] = new p.default('0,0'))),
      ]).then(() => {
        this.columnTypes = types;
        this.vGrid = m.VGrid;
      });
    });
  },
  methods: {
    afterEdit() {
      console.log(this.source)
    }
  }
};
</script>
<style scoped>
.tile {
  width: 100%;
  height: 500px;
}
</style>
