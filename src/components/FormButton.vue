<template>
  <button
    type="button"
    class="h-12 px-2 py-2 text-sm font-bold text-white bg-purple-500 rounded"
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