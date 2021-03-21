<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButton"
      >Stored Bookmarks</base-button
    >
    <base-button @click="setSelectedTab('add-resource')" :mode="addResButton"
      >Add Bookmarks</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource
  },
  computed: {
    storedResButton() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButton() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    }
  },

  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: []
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResources: this.deleteResources
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: link
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    deleteResources(resId) {
      const resIndex = this.storedResources.findIndex(res => res.id === resId);
      this.storedResources.splice(resIndex, 1);
    }
  }
};
</script>
