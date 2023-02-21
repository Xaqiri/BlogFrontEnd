<script setup lang="ts">
import axios from "axios";
import { ref } from "vue";

const user = ref("");
const pass = ref("");
const newUser = async () => {
  user.value = await axios.post(
    `http://localhost:8080/user?name=${user.value}&password=${pass.value}`
  );
  user.value = "";
  pass.value = "";
};
</script>

<template>
  <header>Sign up</header>
  <form @submit.prevent="newUser">
    <input v-model="user" type="text" name="user" />
    <input v-model="pass" type="text" name="password" />
    <button>Submit</button>
  </form>
</template>

<style scoped>
header {
  font-size: 32pt;
  color: hsla(200, 100%, 80%, 1);
}

form {
  display: flex;
  flex-direction: column;
  align-items: left;
  width: 50%;
  gap: 0.5em;
}

input {
  border: 2px solid hsla(200, 100%, 80%, 1);
  background: var(--color-background);
  color: hsla(200, 100%, 80%, 1);
  font-size: 16pt;
}

input:focus {
  outline: none;
}

button {
  border: none;
  background-color: hsla(200, 100%, 80%, 0.5);
  color: hsla(200, 100%, 80%, 1);
  transition: 0.4s;
  font-size: 16pt;
}

@media (hover: hover) {
  button:hover {
    border: 2px solid hsla(200, 100%, 80%, 1);
    box-sizing: border-box;
  }

  .shaded:hover {
    color: hsla(200, 100%, 80%, 0.5);
  }
}
</style>
