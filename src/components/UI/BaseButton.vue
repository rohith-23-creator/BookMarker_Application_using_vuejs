<template>
  <button :type="type" :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ['type', 'mode']
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.75rem;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  background-color: #fe0365;
  border: 1px solid #fe0365;
  color: #fff;
  cursor: pointer;
  font-size: 16px;
}

button:hover,
button:active {
  background-color: #e7246f;
  border-color: #e7246f;
}

button:focus {
  outline: #fe0365;
}

.flat {
  background-color: transparent;
  color: #bb064b;
  border: none;
}

.flat:hover,
.flat:active {
  color: #f8b3ce;
}
</style>
