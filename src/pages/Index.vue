<template>
  <Layout>
    <div class="flex flex-wrap justify-center bg-gray-300">
      <div class="sm:w-full md:w-1/2 lg:w-1/2 xl:w-1/3 mb-4 bg-white">
        <header id="header">
          <h1 class="text-2xl">Case Logger</h1>
        </header>
        <form class="flex flex-col">
          <section class="flex flex-col" id="patient">
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
          </section>
          <section class="flex w-full" id="procedure">
            <div class="flex flex-row"></div>
          </section>
        </form>
      </div>
    </div>
  </Layout>
</template>

<script>
import FormInput from "~/components/FormInput.vue";

export default {
  components: {
    FormInput
  },
  data: {},
  metaInfo: {
    title: "Hello, world!"
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
