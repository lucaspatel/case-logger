<template>
  <input
    v-bind="bind"
    class="w-full h-12 pl-4 m-1 border border-gray-400 rounded"
    :placeholder="title"
  />
</template>

<script>
export default {
  name: "FormInput",
  props: ["title", "bind"],
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