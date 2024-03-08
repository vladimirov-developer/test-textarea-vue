<template>
  <div class="textarea__counter">{{ count }} / {{ maxLength }}</div>
</template>

<script>
import { computed } from 'vue';

export default {
  props: {
    value: String,
    maxLength: Number,
  },
  setup(props) {
    const count = computed(() => props.value.length);

    return { count };
  },
};
</script>

<style lang="scss" src="../assets//scss/symbols-counter.scss" scoped></style>
