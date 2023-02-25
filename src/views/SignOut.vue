<script setup lang="ts">
import { activeUser } from "@/stores/username";
import { onMounted } from "vue";
import router from "@/router";
activeUser.activeUser = ""
onMounted(() => {
  setTimeout(() => {
    router.push("/")
  }, 1000)
})
</script>

<template>
  <div>Signed out</div>
</template>