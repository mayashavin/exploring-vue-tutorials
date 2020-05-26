<template>
  <div class="card" @click="toggleSelect">
    <h3>{{ title }}</h3>
    <img :src="image" />
    <img :src="selectedIcon" class="select-icon" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: "Sample pokemon",
      image:
        "https://res.cloudinary.com/mayashavin/image/upload/v1562279388/pokemons/br5xigetaqosvwf1r1eb.jpg",
      //Flag property to keep track if component is selected
      isSelected: false
    };
  },
  methods: {
    toggleSelect() {
      this.isSelected = !this.isSelected;
    }
    //selectedIcon() {
    //return this.isSelected
    //? "https://res.cloudinary.com/mayashavin/image/upload/w_24,ar_1:1,c_scale/v1566137286/ExploringVueJS/check-circle-solid.png"
    //: "https://res.cloudinary.com/mayashavin/image/upload/w_24,ar_1:1,c_scale/v1566137284/ExploringVueJS/circle-regular.png";
    //}
  },
  computed: {
    selectedIcon() {
      return this.isSelected
        ? "https://res.cloudinary.com/mayashavin/image/upload/w_24,ar_1:1,c_scale/v1566137286/ExploringVueJS/check-circle-solid.png"
        : "https://res.cloudinary.com/mayashavin/image/upload/w_24,ar_1:1,c_scale/v1566137284/ExploringVueJS/circle-regular.png";
    }
  }
  // watch: {
  //   isSelected(val) {
  //     console.log(val);
  //   }
  // }
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
