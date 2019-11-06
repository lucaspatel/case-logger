<template>
  <button class="h-12 bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "FormButton",
  props: {
    color: {
      type: String,
      default: "bg-purple-500"
    }
  },
  data() {
    return {
      message: "Try change me!"
    };
  },
  methods: {
    onClick() {
      this.message = "Here you go :)";
    }
  }
};
</script>

<style>
</style>