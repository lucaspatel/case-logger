<template onload="addDateListener()">
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
              <form-input title="Date" :model="date" type="datetime-local" id="date" onchange="allignDates()" ></form-input>
            </div>
            <div class="flex flex-row">
              <form-input title="MRN" :bind="mrn"></form-input>
              <form-input title="Initials" :bind="initials"></form-input>
            </div>
            <div class="flex flex-row">
              <form-input title="Facility" :bind="facility"></form-input>
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
          </section>
        </form>
      </div>
    </div>
  </Layout>
</template>

<script>
import FormInput from "~/components/FormInput.vue";
import FormButton from "~/components/FormButton.vue";
import BlockLineGroup from "~/components/BlockLineGroup.vue";

export default {
  components: {
    FormInput: FormInput,
    FormButton: FormButton,
    BlockLineGroup: BlockLineGroup
  },
  data() {
    return {
      date: "12/02/1997",
      mrn: "",
      initials: "",
      facility: "",
      anesthesiaStart: "",
      anesthesiaEnd: "",
      blockLines: [],
      notes: ""
    };
  },
  methods: {
    addDateListener: function () {
      const $source = document.querySelector("#date");
      const $result = document.querySelector("#anesthesiaStart");

      const typeHandler = function(e) {
        $result.innerHTML = e.target.value;
      };

      $source.addEventListener("input", typeHandler); // register for oninput
      $source.addEventListener("propertychange", typeHandler); // for IE8
    }
  },
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
