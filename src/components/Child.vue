<template>
  <div>{{ childProps.a }}</div>
</template>

<script>
export default {
  name: "child",
  props: {
    childProps: {
      type: Object,
      default: () => ({}),
    },
  },
  watch: {
    childProps: {
      handler(val, oldVal) {
        console.log("child props childProps update");
      },
      deep: true,
    },
  },
};
</script>
