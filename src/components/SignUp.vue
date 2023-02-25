<script setup lang="ts">
import axios from "axios";
import { ref } from "vue";

const message = ref("Sign up");
const user: any = ref("");
const pass = ref("");
const newUser = async () => {
  user.value = await axios(
    `https://topmembersonly.up.railway.app/api/signup`,
    {
      method: "post",
      data: { first_name: "none", last_name: "none", username: user.value, password: pass.value},
      headers: {
      Accept: "application/json",
        "Content-Type": "application/json",
        mode: "cors",
        "Access-Control-Allow-Origin": "*",
      },
    }
  ).then(resp => resp.data)
    .then(resp => console.log(resp))
    .catch((err) => (message.value = `Error ${err.response.status}: ${err.response.data.error}`));
  user.value = "";
  pass.value = "";
};
</script>

<template>
  <header>{{ message }}</header>
  <form @submit.prevent="newUser">
    <input v-model="user" type="text" name="user" placeholder="name" required />
    <input
      v-model="pass"
      type="text"
      name="password"
      placeholder="password"
      required
    />
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
  transition: 0.4s;
}

input:focus {
  outline: none;
}

.invalid {
  border-color: hsla(0, 100%, 60%, 1);
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
