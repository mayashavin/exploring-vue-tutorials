<template>
  <div class="card" @click="toggleSelect">
    <h3>{{ displayTitle }}</h3>
    <img :src="image" />
    <img :src="selectedIcon" class="select-icon" />
  </div>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    image: {
      type: String,
      default:
        "https://res.cloudinary.com/mayashavin/image/upload/w_120,c_scale,q_auto,f_auto/v1590528615/ExploringVueJS/placeholder"
    }
  },
  data() {
    return {
      isSelected: false
    };
  },
  methods: {
    toggleSelect() {
      this.$emit("update-select", this.title);
      this.isSelected = !this.isSelected;
    }
  },
  computed: {
    selectedIcon() {
      return this.isSelected
        ? "https://res.cloudinary.com/mayashavin/image/upload/w_24,ar_1:1,c_scale/v1566137286/ExploringVueJS/check-circle-solid.png"
        : "https://res.cloudinary.com/mayashavin/image/upload/w_24,ar_1:1,c_scale/v1566137284/ExploringVueJS/circle-regular.png";
    },
    displayTitle() {
      return `${this.title.charAt(0).toUpperCase()}${this.title.slice(1)}`;
    }
  }
};
</script>
<style scoped lang="scss">
.card {
  position: relative;
  border: 1px solid lightgray;
  padding: 5px;
  margin-right: 10px;
  margin-bottom: 10px;
  width: 220px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.2);

  &:hover {
    background-color: #d3d3d363;
    cursor: pointer;
  }
}

.select-icon {
  position: absolute;
  top: 0px;
  right: 0px;
  margin: 5px;
}
</style>
