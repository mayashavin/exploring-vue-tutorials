<template>
  <div class="home">
    <search :search-term="searchTerm" @input="onChange" />
    <!-- <pokemon-card :title="jigglypuff.title" :image="jigglypuff.image" /> -->
    <!-- <pokemon-card :title="eevee.title" :image="eevee.image" /> -->
    <!-- <pokemon-card v-bind="jigglypuff" /> -->
    <pokemon-card :title="jigglypuff.title" />
    <pokemon-card v-bind="eevee" />
    <!-- <pokemon-card :title="jigglypuff.title" :image="jigglypuff" /> -->
  </div>
</template>

<script>
// @ is an alias to /src
import PokemonCard from "@/components/PokemonCard.vue";
import Search from "@/components/Search.vue";

export default {
  name: "home",
  components: {
    PokemonCard,
    Search
  },
  data() {
    return {
      jigglypuff: {
        title: "Jigglypuff",
        image:
          "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/jigglypuff.png"
      },
      eevee: {
        title: "Eevee",
        image:
          "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/eevee.png"
      },
      searchTerm: ""
    };
  },
  methods: {
    onChange(val) {
      this.searchTerm = val;
      // eslint-disable-next-line no-console
      console.log(this.searchTerm);
    }
  }
};
</script>
