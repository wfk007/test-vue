<template>
  <child :child-props="childProps" />
</template>

<script>
import { computed, defineComponent, toRefs, watch } from "@vue/composition-api";
import Child from "./Child.vue";
// hooks
function useBizData(infos) {
  const childProps = computed(() => [0, ...infos.value.childProps]);
  return {
    childProps,
  };
}
export default defineComponent({
  name: "middle",
  components: {
    Child,
  },
  props: {
    infos: {
      type: Object,
      default: () => ({}),
    },
  },
  setup(props) {
    const { infos } = toRefs(props);
    const { childProps } = useBizData(infos);
    watch(infos, () => {
      console.log("middle infos update");
    });
    watch(childProps, () => {
      console.log("middle childProps update");
    });
    return {
      childProps,
    };
  },
});
</script>
