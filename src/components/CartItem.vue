<template></template>
<script>
export default {
  name: "CartItem",
  props: {
    initialItem: Object,
  },
  data() {
    return {
      items: this.initialItem,
    };
  },
};
</script>
