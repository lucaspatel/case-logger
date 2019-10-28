<template>
  <div class="layout bg-gray-300">
    <slot />
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style>
</style>
