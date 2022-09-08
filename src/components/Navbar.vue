<template>
  <ndiv id="nav">
    <router-link to="/">
      <img src="" alt="logo" id="logo" />
    </router-link>
    <router-link to="/">Home</router-link> |
    <router-link to="/orders">Orders</router-link>
  </ndiv>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style scoped></style>
