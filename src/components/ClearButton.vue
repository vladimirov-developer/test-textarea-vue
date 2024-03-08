<template>
  <button @click="clearText" class="clear-button">Очистить</button>
</template>

<script>
export default {
  props: {
    onClick: Function,
  },
  methods: {
    clearText() {
      this.onClick();
    },
  },
};
</script>

<style lang="scss" src="../assets/scss/clear-button.scss" scoped></style>
