<template>
  <button
    type="button"
    class="h-12 bg-purple-500 text-white text-sm font-bold py-2 px-2 rounded"
    :disabled="disabled"
    :class="{ disabled: disabled, 'md:hover:bg-purple-700': !disabled }"
    @click="action"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "FormButton",
  props: {
    color: String,
    action: Function,
    disabled: Boolean
  },
  data() {
    return {};
  },
  methods: {}
};
</script>

<style lang="css">
.disabled {
  @apply opacity-50;
  @apply cursor-not-allowed;
}
</style>