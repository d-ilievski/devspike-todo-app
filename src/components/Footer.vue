<template>
  <footer>
    <div>&copy; DevSpike Community</div>
    <router-link to="/about">About</router-link>
  </footer>
</template>

<script>
export default { name: "Task" };
</script>

<style scoped>
footer {
  text-align: center;
  margin-top: 32px;
  color: grey;
}

a {
  color: teal;
}
</style>