<template>
  <div>{{ childProps.join("-") }}</div>
</template>

<script>
export default {
  name: "child",
  props: {
    childProps: {
      type: Array,
      default: () => [],
    },
  },
  watch: {
    childProps: {
      handler() {
        console.log("child props childProps update");
      },
      deep: true,
    },
  },
};
</script>
