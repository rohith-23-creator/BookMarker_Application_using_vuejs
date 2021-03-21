<template>
  <base-dialog v-if="inputIsInvalid" title="Invalid Input :(">
    <template #default>
      <p>
        Unfortunately, atleast one or more input you entered is invalid.
      </p>
      <p>
        Kindly Fill all the fields of the input.
      </p>
    </template>
    <template #actions>
      <base-button @click="setValidInput">Got It :)</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="title">Description</label>
        <textarea name="description" id="description" rows="3" ref="desInput" />
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" ref="linkInput" />
      </div>
      <base-button type="submit">Add Bookmark</base-button>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResource'],
  data() {
    return {
      inputIsInvalid: false
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.desInput.value;
      const enteredLink = this.$refs.linkInput.value;

      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredLink.trim() === ''
      ) {
        this.inputIsInvalid = true;
        return;
      }
      this.addResource(enteredTitle, enteredDescription, enteredLink);
    },
    setValidInput() {
      this.inputIsInvalid = false;
    }
  }
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
  font-size: 1.2rem;
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
  border-color: #e7634f;
}
.form-control {
  margin: 1rem 0;
}

base-button {
  margin-top: 1rem;
}
</style>
