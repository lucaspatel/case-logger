<template>
  <Layout>
    <div class="flex flex-wrap justify-center bg-gray-200">
      <div class="w-full sm:w-full md:w-1/2 lg:w-1/2 xl:w-1/3 px-2 bg-white">
        <header id="header">
          <h1 class="text-4xl mx-1 py-8">Case Logger</h1>
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
            <div class="inline-flex flex-row">
              <textarea
                :model="notes"
                class="w-full h-24 m-1 mb-8 pl-4 pt-3 border border-gray-400 rounded"
                placeholder="Additional Notes"
              ></textarea>
            </div>
          </section>
          <section class="flex flex-col" id="controls">
            <div class="flex justify-center">
              <v-button class="m-1 w-1/2">Add Block </v-button>
              <v-button class="m-1 w-1/2">Add Line</v-button>
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

export default {
  components: {
    FormInput: FormInput,
    "v-button": FormButton
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
