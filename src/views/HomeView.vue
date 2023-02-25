<script setup lang="ts">
import { onMounted, type Ref, ref } from "vue";
import axios from "axios";
import { activeUser } from "@/stores/username";
const username = activeUser.activeUser
let message: Ref<string> = ref("Welcome to the message board");
const todos = ref([]);
onMounted(async () => {
  todos.value = await axios(
    "https://topmembersonly.up.railway.app/api/messages",
    {
      method: "get",
      headers: {
        withCredentials: false,
        mode: "no-cors",
        "Access-Control-Allow-Origin": "*",
      },
    }
  )
    .then((resp) => resp.data)
    .catch((err) => (message.value = err));
  todos.value = todos.value.reverse();
});
</script>
<template>
  <header v-if="username === ''">Welcome to the message board</header>
  <header v-else>Welcome back, {{ username }}</header>
  <div>
    <ul>
      <li v-for="todo in todos" class="card" :key="todo.id">
        <div id="todoTop">
          <div class="todoTitle">{{ todo.title }}</div>
          <button>X</button>
        </div>
        <div class="todoBody">{{ todo.body }}</div>
        <div class="todoUser">{{ todo.user }}</div>
        <div class="todoTimestamp">{{ todo.timestamp }}</div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
header {
  font-size: 32pt;
  color: hsla(200, 100%, 80%, 1);
}

ul {
  margin: 1em;
}

li {
  list-style: none;
  margin-bottom: 0.5em;
}

.card {
  border: 1px solid hsla(200, 100%, 80%, 1);
  padding: 0.5em 1em;
  color: hsla(200, 100%, 80%, 0.6);
}

.card:hover {
  background-color: hsla(200, 100%, 80%, 0.1);
  color: hsla(200, 100%, 80%, 0.8);
}

button {
  border: none;
  background-color: black;
  color: hsla(200, 100%, 80%, 1);
  width: 25%;
}

#todoTop {
  display: flex;
  justify-content: space-between;
  font-size: 1em;
}

.todoTitle {
  font-size: 1.5em;
  color: hsla(200, 100%, 80%, 1);
  margin-left: 1.5em;
  width: 75%;
}
</style>
