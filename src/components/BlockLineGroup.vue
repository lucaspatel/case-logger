<template>
  <section class="flex flex-col" id="procedure">
    <div class="block-template">
      <div class="flex flex-row">
        <form-input :title="'Block / Line ' + id" :model="bl.name"></form-input>
      </div>
      <div class="flex flex-row">
        <form-input :title="'Block / Line ' + id + ' Start'" :model="bl.start"></form-input>
        <form-input :title="'Block / Line ' + id + ' End'" :model="bl.end"></form-input>
      </div>
    </div>
  </section>
</template>

<script>
import FormInput from "~/components/FormInput.vue";

export default {
  components: {
    FormInput: FormInput
  },
  name: "BlockLineGroup",
  props: ["id", "bl"],
  data() {
    return {};
  },
  methods: {}
};
</script>

<style>
</style>