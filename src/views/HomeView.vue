<script setup lang="ts">
import { onMounted, type Ref, ref } from "vue";
import axios from "axios";

let test: string | any = ref("");

// test.value = await fetch("http://localhost:8080/user", {
//   mode: "cors",
//   method: "GET",

//   // headers: {
//   //   Accept: "application/json",
//   //   "Content-Type": "application/json",
//   // },
// })
//   .then((res) => {
//     return res.text();
//   })
//   .then((resp) => {
//     console.log(resp);
//     return resp;
//   })
//   .catch((e) => {
//     console.log(e);
//   });
test.value = await axios
  .get("http://localhost:8080/user")
  .then((res) => res.data);
</script>

<template>
  <main>
    <div>{{ test }}</div>
  </main>
</template>
