<template>
  <button
    class="m-1 w-1/2 h-12 bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-4 rounded"
  >{{ message }}</button>
</template>

<script>
export default {
  name: "FormButton",
  props: ["message", "color"],
  data() {
    return {
      retMessage: "This is it"
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