<template>
  <the-header :title="title"></the-header>
  <the-resources></the-resources>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';

export default {
  components: {
    TheHeader,
    // eslint-disable-next-line vue/no-unused-components
    TheResources
  },
  data() {
    return {
      title: 'Bookmarker Application'
    };
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0%;
  padding: 0;
}

body {
  font-family: sans-serif;
}
</style>
