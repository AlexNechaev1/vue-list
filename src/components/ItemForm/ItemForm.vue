<template>
  <form class="form-container" v-on:submit.prevent="onSubmit">
    <input placeholder="Item name" v-on:input="onNameChange" ref="nameInput" />
    <input
      placeholder="Item Description"
      v-on:input="onDescriptionChange"
      ref="descriptionInput"
    />
    <button>Add</button>
  </form>
</template>

<script>
export default {
  name: "ItemForm",
  date() {
    return {
      name: "",
      description: "",
    };
  },
  methods: {
    onNameChange(event) {
      this.name = event.target.value;
    },
    onDescriptionChange(event) {
      this.description = event.target.value;
    },
    onSubmit() {
      if (
        this.name.trim("").length > 0 &&
        this.description.trim("").length > 0
      ) {
        this.$emit("onSubmit", {
          id: Math.floor(Math.random() * 100000) + "",
          name: this.name,
          description: this.description,
        });
        this.$refs.nameInput.value = "";
        this.$refs.descriptionInput.value = "";
      }
    },
  },
};
</script>

<style scoped>
.form-container {
  display: flex;
  justify-content: space-evenly;
  margin: 0 20rem;
  padding: 3rem;
}
input {
  border: none;
  outline: none;
  width: 20rem;
  border-bottom: 3px solid #43b883;
  margin: 0 0.2rem;
  padding: 0.5rem 1rem;
}
input:focus {
  
  border-left: 3px solid #43b883;
  border-bottom-left-radius: 1rem;
  
  
}
button {
  border: 3px solid #43b883;
  border-radius: 1rem;
  padding: 1rem 3rem;
  background-color: white;
}
button:hover {
  border: 5px solid #43b883;
  background-color: #43b883;
  color: white;
}
</style>
