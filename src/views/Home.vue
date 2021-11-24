<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <child :child-props="infos.childProps || {}" />
    <button @click="btnClick">add a field in item</button>
  </div>
</template>

<script>
import Child from "@/components/Child.vue"; // @ is an alias to /src

export default {
  name: "parent",
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
          childProps: {
            a: 1,
            b: 2,
            c: 3,
          },
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
  },
  watch: {
    infos: function (newQuestion, oldQuestion) {
      console.log("parent infos update");
    },
    "infos.childProps": function (newQuestion, oldQuestion) {
      console.log("parent infos.childProps update");
    },
  },
};
</script>
