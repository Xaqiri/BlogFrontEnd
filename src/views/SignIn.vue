<script setup lang="ts">
import SignIn from "../components/SignIn.vue";
</script>
<template>
  <div class="about">
    <SignIn />
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
