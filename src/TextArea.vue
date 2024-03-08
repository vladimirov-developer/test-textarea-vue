<template>
  <div class="textarea">
    <label class="textarea__label">Текст перед полем ввода</label>

    <div class="textarea__wrapper" :class="{ 'textarea--error': isMaxLengthExceeded, 'loading': isLoading }">
      <textarea
          v-model="value"
          @input="handleInput"
          @focus="isFocused = true"
          @blur="isFocused = false"
          :class="{ 'textarea--error': isMaxLengthExceeded }"
          class="textarea__field"
          required
      ></textarea>
      <span class="textarea__placeholder">Название поля</span>
    </div>

    <div v-if="isMaxLengthExceeded" class="textarea__error-text">Ошибка</div>
    <SymbolsCounter :value="value" :maxLength="maxLength" />
    <ClearButton @click="clearText" />
  </div>
</template>

<script>
import { ref, computed } from 'vue';
import SymbolsCounter from './components/SymbolsCounter.vue';
import ClearButton from './components/ClearButton.vue';

export default {
  components: {
    SymbolsCounter,
    ClearButton,
  },
  props: {
    maxLength: {
      type: Number,
      default: 1000,
    },
  },
  setup(props) {
    const value = ref('');
    const isFocused = ref(false);

    const isLoading = true;

    const isMaxLengthExceeded = computed(() => value.value.length > props.maxLength);

    function handleInput(event) {
      value.value = event.target.value;
    }

    function clearText() {
      value.value = '';
    }

    return {
      value,
      isFocused,
      isLoading,
      isMaxLengthExceeded,
      handleInput,
      clearText,
    };
  },
};
</script>

<style lang="scss" src="./assets/scss/text-area.scss" scoped></style>
