<template>
  <section class="flex flex-col mb-8" id="procedure">
    <p class="mx-1">Procedure</p>
    <div class="flex flex-row">
      <form-input title="Anesthesia Start" :model="anesthesiaStart"></form-input>
      <form-input title="Anesthesia End" :model="anesthesiaEnd"></form-input>
    </div>
    <div class="block-template">
      <div class="flex flex-row">
        <form-input title="Block" :model="blockNum"></form-input>
      </div>
      <div class="flex flex-row">
        <form-input title="Block Start" :model="blockStart"></form-input>
        <form-input title="Block End" :model="blockEnd"></form-input>
      </div>
      <div class="line-template">
        <div class="flex flex-row">
          <form-input title="Line" :model="lineNum"></form-input>
        </div>
        <div class="flex flex-row">
          <form-input title="Line Start" :model="lineStart"></form-input>
          <form-input title="Line End" :model="lineEnd"></form-input>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import FormInput from "~/components/FormInput.vue";

export default {
  components: {
    FormInput: FormInput,
  },
  name: "BlockLineGroup",
  props: ["model"],
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