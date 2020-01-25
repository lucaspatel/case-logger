<template>
  <div class="layout bg-gray-300 max-h-100">
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
