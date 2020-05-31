<template>
  <div>
    <label for="search" class="search-label">Search for Pokemon: </label>
    <input
      name="search"
      v-model="term"
      arial-label="Search for Pokemon"
      placeholder="Search for Pokemon"
      @input="onInput"
    />
  </div>
</template>
<script>
export default {
  props: {
    searchTerm: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      term: this.searchTerm
    };
  },
  methods: {
    onInput($event) {
      this.$emit("input", $event.target.value);
    }
  }
};
</script>
<style scoped>
.search-label {
  margin-right: 10px;
}

input {
  padding: 10px;
  font-size: 1rem;
  margin: 10px;
}
</style>
