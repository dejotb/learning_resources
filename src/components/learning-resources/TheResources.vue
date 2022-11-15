<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('add-resource')" :mode="addButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab" :resources="storedResources"></component>
  </keep-alive>
</template>

<script>
import AddResource from './AddResource.vue';
import storedResources from './StoredResources.vue';

export default {
  components: { AddResource, storedResources },

  props: ['resources'],

  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Vue Official guide',
          description: 'the official Vue.js documentation',
          link: 'vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'the official google documentation',
          link: 'google.com',
        },
      ],
    };
  },

  provide() {
    return {
      addResource: this.addResource,
    };
  },

  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
      console.log(this.selectedTab);
    },

    addResource(title, desc, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: desc,
        link: url,
      };

      this.storedResources.push(newResource);
      this.selectedTab = 'stored-resources';
    },
  },
};
</script>
