<template>
  <div class="home">
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

export default {
  name: "home",
  components: {
    PokemonCard
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
      }
    };
  }
};
</script>
