<template>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template #default>
      <p>Unfortunately, at least one input value is invalid</p>
      <p>Please check all inputs</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <h2>Add Resource</h2>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="title" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="description"
        />
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="link" />
      </div>
      <base-button type="submit">Add Resource</base-button>
    </form>
  </base-card>
</template>

<script>
export default {
  //   props: ['resources'],

  data() {
    return {
      inputIsInvalid: false,
    };
  },

  inject: ['addResource'],

  methods: {
    submitData() {
      const enteredTitle = this.$refs.title.value;
      const enteredDescription = this.$refs.description.value;
      const enteredLink = this.$refs.link.value;

      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredLink === ''
      ) {
        this.inputIsInvalid = true;
        return;
      }

      this.addResource(enteredTitle, enteredDescription, enteredLink);
    },

    confirmError() {
      this.inputIsInvalid = false;
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
