<template>
  <footer id="footer">
    <p>Make Your Burguer &copy; 2022</p>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style scoped>
#footer {
  height: 100px;
  background-color: #222;
  border-top: 4px sild #111;
  color: #fcba03;
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  bottom: 0;
  width: 100%;
}
</style>
