<template>
  <input
    v-model="term"
    arial-label="Search for Pokemon"
    placeholder="Search for Pokemon"
    @input="onInput"
  />
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
  // computed: {
  //   term() {
  //     return this.searchTerm;
  //   }
  // }
};
</script>
