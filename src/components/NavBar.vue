<script setup lang="ts">
import { activeUser } from "@/stores/username";
</script>

<template>
  <nav id="nav-bar">
    <div class="shaded"><RouterLink to="/">Blog</RouterLink></div>
    <div id="nav-links">
      <div v-if="activeUser.activeUser ===''">
        <RouterLink to="/signup">Sign Up</RouterLink>
        <RouterLink to="/signin">Sign In</RouterLink>
      </div>
      <div v-else>
        <RouterLink to="/post">Post</RouterLink>
        <RouterLink to="/signout">Sign Out</RouterLink>
      </div>
    </div>

    <!-- <RouterLink to="/clicker">Clicker</RouterLink> -->
  </nav>
</template>

<style scoped>
#nav-bar {
  width: 100%;
  padding: 0 0.5em;
  font-size: 24pt;
  display: flex;
  border-bottom: 2px solid cyan;
  justify-content: space-between;
  align-items: center;
  color: hsla(200, 100%, 80%, 0.5);
  cursor: default;
}

#nav-links div {
  display: flex;
  font-size: 16pt;
  gap: 0.5em;
}

a,
.shaded {
  text-decoration: none;
  color: hsla(200, 100%, 80%, 1);
  transition: 0.4s;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
  color: hsla(200, 100%, 80%, 0.5);
  /* cursor: default; */
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(200, 100%, 80%, 0.5);
  }

  .shaded:hover {
    color: hsla(200, 100%, 80%, 0.5);
  }
}
</style>
