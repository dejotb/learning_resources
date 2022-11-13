<template>
  <stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
import storedResources from './components/learning-resources/StoredResources.vue';

export default {
  components: { storedResources },

  data() {
    return {
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
