<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
import TestComponent from "./components/TestComponent.vue";
import TestSlot from "./components/TestSlot.vue";

import { ref } from "vue";

const name = ref("Ram");
const list1 = ref(["Sam", "Hari", "Sita"]);
const sales = ref({ Sam: 100, Hari: 200, Sita: 300 });
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="@/assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <TestComponent testProps="TestProps String" />
      <TestSlot v-slot:default>Default Slot</TestSlot>
      <TestSlot v-slot:paragrph>paragraph Slot</TestSlot>
      <h1>{{ name }}</h1>
      <ul>
        <li v-for="(i, index) in list1" :key="index">{{ i }}</li>
      </ul>

      <ul>
        <li v-for="(sale, index) in sales" :key="index">{{ sale }}</li>
      </ul>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/store">Store</RouterLink>
        <RouterLink to="/cart">Cart</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
