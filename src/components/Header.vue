<template>
  <header>
    <div>Covid 19 Tracker</div>
    <span class="h-small"
      >API by <a href="covid19api.com">covid19api.com</a></span
    >
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
header {
  background: darkslateblue;
  font-size: 2em;
  font-weight: 600;
  color: white;
  padding: 0.5em 0;
}
.h-small {
  font-size: 0.4em;

  a {
    font-weight: 100;
    color: white;
    opacity: 0.8;
    text-decoration: none;
  }
}
</style>
