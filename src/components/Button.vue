<template>
  <button
    class="w-full h-12 bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded"
  >Save</button>
</template>

<script>
export default {
  name: "FormButton",
  props: [""],
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