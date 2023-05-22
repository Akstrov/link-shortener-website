<script setup>
import { RouterView } from 'vue-router'
//theme
import 'primevue/resources/themes/lara-light-indigo/theme.css'

//core
import 'primevue/resources/primevue.min.css'
</script>
<style>
body {
  font-family: var(--font-family);
}
</style>
<template>
  <RouterView />
</template>
