<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ['title']
};
</script>

<style scoped>
header {
  width: 100%;
  height: 5rem;
  background-color: #fe0365;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
}

header h1 {
  margin: 0;
}
</style>
