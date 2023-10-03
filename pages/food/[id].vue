<template>
  <div>
    <h1>Parameter: {{ id }}</h1>
  </div>
</template>

<script>
import { onMounted } from "vue";
import { useRoute } from "vue-router";
export default {
  setup() {
    const route = useRoute();
    const id = route.params.id;

    onMounted(() => {
        console.log(id)
    })

    return {
      id,
    };
  },
};
</script>
