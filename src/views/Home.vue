<template>
  <div>
    <child :child-props="childProps" />
    <button @click="btnClick">add a field in item</button>
  </div>
</template>

<script>
import Child from "@/components/Child.vue"; // @ is an alias to /src

export default {
  name: "home",
  components: {
    Child,
  },
  data: function () {
    return {
      item: {
        name: "wfk",
        infos: {
          a: 111,
          b: 222,
          c: 333,
          childProps: [1, 2, 3],
        },
      },
    };
  },
  methods: {
    btnClick() {
      this.$set(this.item, "age", 18);
    },
  },
  computed: {
    infos: function () {
      return this.item.infos || {};
    },
    childProps: function () {
      return [0, ...this.infos.childProps];
    },
  },
  watch: {
    infos: function () {
      console.log("parent infos update");
    },
    childProps: function () {
      console.log("parent childProps update");
    },
  },
};
</script>
