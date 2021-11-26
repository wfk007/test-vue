<template>
  <div>
    <!-- <middle :infos="infos" /> -->
    <child :child-props="infos.childProps" />
    <button @click="btnClick">add a field in item</button>
  </div>
</template>

<script>
import {
  computed,
  defineComponent,
  ref,
  set,
  watch,
} from "@vue/composition-api";
import Middle from "@/components/Middle.vue";
import Child from "@/components/Child.vue";

// component
export default defineComponent({
  name: "composition-api",
  components: {
    Middle,
    Child,
  },
  setup() {
    const item = ref({
      name: "wfk",
      infos: {
        a: 111,
        b: 222,
        c: 333,
        childProps: [1, 2, 3],
      },
    });
    const infos = computed(() => item.value.infos || {});

    infos.value.childProps = [0, ...infos.value.childProps];

    // const childProps = computed(() => );

    const btnClick = () => {
      set(item.value, "age", 18);
    };
    watch(item, () => {
      console.log("parent item update");
    });
    watch(infos, () => {
      console.log("parent infos update");
    });
    return {
      item,
      infos,
      // childProps,
      btnClick,
    };
  },
});
</script>
