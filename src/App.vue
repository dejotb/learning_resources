<template>
  <the-header title="RememberMe"></the-header>
  <the-resources></the-resources>
  <!-- <add-resource :resources="addResource"></add-resource> -->
  <!-- <stored-resources :resources="storedResources"></stored-resources> -->
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';

export default {
  components: { TheHeader, TheResources },

  emits: ['resource-tab'],
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
