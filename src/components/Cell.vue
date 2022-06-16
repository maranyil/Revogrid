<template>
  <button v-on:click="iAmClicked">You clicked me {{ count }} times.</button>
</template>
<script>

// your vue component
export default {
  // access any cell properties here
  props: ["rowIndex", "prop"],
  name: "Cell",
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    iAmClicked() {
      this.count++;
    },
  }
};
</script>
