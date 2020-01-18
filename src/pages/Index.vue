<template>
  <Layout>
    <div class="flex flex-wrap justify-center bg-gray-200">
      <div class="w-full px-2 bg-white sm:w-full md:w-1/2 lg:w-1/2 xl:w-1/3">
        <header id="header">
          <h1 class="py-8 mx-1 text-4xl">Case Logger</h1>
        </header>
        <form class="flex flex-col">
          <section class="flex flex-col mb-8" id="patient">
            <p class="mx-1">Patient</p>
            <div class="flex flex-row">
              <form-input title="Date" :model="date"></form-input>
            </div>
            <div class="flex flex-row">
              <form-input title="MRN" :model="mrn"></form-input>
            </div>
            <div class="flex flex-row">
              <form-input title="First Name" :model="firstName"></form-input>
              <form-input title="Last Name" :model="lastName"></form-input>
            </div>
            <div class="flex flex-row">
              <form-input title="Facility" :model="facility"></form-input>
            </div>
          </section>
          <block-line-group></block-line-group>
          <block-line-group></block-line-group>
          <div class="flex-row">
            <textarea
              :model="notes"
              class="w-full h-24 pt-3 pl-4 m-1 mb-8 border border-gray-400 rounded"
              placeholder="Additional Notes"
            ></textarea>
          </div>
          <section class="flex flex-col" id="controls">
            <div class="flex justify-center">
              <v-button class="w-1/2 m-1">Add Block</v-button>
              <v-button class="w-1/2 m-1">Add Line</v-button>
            </div>
            <v-button class="m-1">Save</v-button>
          </section>
        </form>
      </div>
    </div>
  </Layout>
</template>

<script>
import FormInput from "~/components/FormInput.vue";
import FormButton from "~/components/Button.vue";
import BlockLineGroup from "~/components/BlockLineGroup.vue";

export default {
  components: {
    FormInput: FormInput,
    "v-button": FormButton,
    BlockLineGroup: BlockLineGroup
  },
  data: {},
  metaInfo: {
    title: "Case Logger"
  }
};
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
body {
  font-family: "Sarabun", sans-serif;
}
</style>
