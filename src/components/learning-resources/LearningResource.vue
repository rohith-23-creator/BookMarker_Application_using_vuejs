<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button mode="flat" @click="deleteResources(id)"
          >Delete</base-button
        >
      </header>
      <p>{{ description }}</p>
      <nav>
        <a :href="link">View Resources</a>
      </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  props: ['id', 'title', 'description', 'link'],
  inject: ['deleteResources']
};
</script>

<style>
li {
  margin: auto;
  max-width: 40rem;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
p {
  margin-right: 1rem 0;
  padding-bottom: 1rem;
}

a {
  text-decoration: none;
  color: #fe0365;
  font-weight: 600;
}

a:hover,
a:active {
  color: #e7246f;
}

h3 {
  font-size: 1.5rem;
  margin: 0.5em 0;
}
</style>
