<script setup lang="ts">
import { onMounted, type Ref, ref } from "vue";
import axios, { AxiosError } from "axios";
import router from "@/router";
import { useLink } from "vue-router";

let test: Ref<string> = ref("");
onMounted(async () => {
  test.value = await axios
    .get("http://localhost:8080/user")
    .then((res) => res.data)
    .catch((err) => err);
});
</script>
<template>
  <header>{{ test }}</header>
  <main>
    <div>{{ test }}</div>
  </main>
</template>

<style scoped>
header {
  font-size: 32pt;
  color: hsla(200, 100%, 80%, 1);
}
</style>
