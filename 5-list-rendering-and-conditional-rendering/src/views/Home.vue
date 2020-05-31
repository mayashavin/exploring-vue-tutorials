<template>
  <div class="home">
    <search :search-term="searchTerm" @input="onChange" />
    <div v-show="hasSelected">
      <h3>Selected pokemons:</h3>
      <span v-for="(selected, index) in selectedPokemons" :key="index">
        {{ selected }}
      </span>
    </div>
    <!-- <div v-else-if="!hasSelected && searchTerm">
      You haven't selected any but search for something.
    </div>
    <div v-else>
      There is no pokemon selected.
    </div> -->
    <!-- <div>
      <div v-for="(text, number) in numbers">
        {{number}}: {{text}}
      </div>
    </div> -->
    <div class="pokemon-list--container">
      <pokemon-card
        v-for="(pokemon, key) in pokemons"
        v-bind="pokemon"
        :key="key"
        @update-select="updateSelectedPokemons"
      />
    </div>
    <!-- <pokemon-card v-for="(pokemon, index) in pokemons" v-bind="pokemon" :key="index"/> -->
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
      // numbers: { 1: "One", 2: "Two", 3: "Three" },
      pokemons: [
        {
          title: "jigglypuff",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/jigglypuff"
        },
        {
          title: "eevee",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/eevee"
        },
        {
          title: "bulbasaur",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/1"
        },
        {
          title: "ivysaur",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/2"
        },
        {
          title: "venusaur",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/3"
        },
        {
          title: "charmander",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/4"
        },
        {
          title: "charizard",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/5"
        },
        {
          title: "squirtle",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/6"
        },
        {
          title: "wartortle",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/7"
        },
        {
          title: "blastoise",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/8"
        },
        {
          title: "caterpie",
          image:
            "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/9"
        }
      ],
      // pokemons: {
      //   jigglypuff: {
      //     title: "jigglypuff",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/jigglypuff"
      //   },
      //   eevee: {
      //     title: "eevee",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/eevee"
      //   },
      //   bulbasaur: {
      //     title: "bulbasaur",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/1"
      //   },
      //   ivysaur: {
      //     title: "ivysaur",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/2"
      //   },
      //   venusaur: {
      //     title: "venusaur",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/3"
      //   },
      //   charmander: {
      //     title: "charmander",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/4"
      //   },
      //   charizard: {
      //     title: "charizard",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590480596/ExploringVueJS/5"
      //   },
      //   squirtle: {
      //     title: "squirtle",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/6"
      //   },
      //   wartortle: {
      //     title: "wartortle",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/7"
      //   },
      //   blastoise: {
      //     title: "blastoise",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/8"
      //   },
      //   caterpie: {
      //     title: "caterpie",
      //     image:
      //       "https://res.cloudinary.com/mayashavin/image/upload/q_auto,f_auto,w_120,c_scale/v1590494324/ExploringVueJS/9"
      //   }
      // },
      searchTerm: "",
      // label: "Pokemon",
      selectedPokemons: []
    };
  },
  methods: {
    onChange(val) {
      this.searchTerm = val;
      // eslint-disable-next-line no-console
      console.log(this.searchTerm);
    },
    updateSelectedPokemons(pokemon) {
      //Check if the pokemon is already selected by getting its index in the list
      const indexOfPokemon = this.selectedPokemons.indexOf(pokemon);

      if (indexOfPokemon !== -1) {
        //Remove it from the selected list if it is already selected
        this.selectedPokemons.splice(indexOfPokemon, 1);
      } else {
        //Add the pokemon to the list
        this.selectedPokemons.push(pokemon);
      }
    }
  },
  computed: {
    hasSelected() {
      return this.selectedPokemons.length > 0;
    }
  }
};
</script>
<style scoped>
.pokemon-list--container {
  display: flex;
  flex-wrap: wrap;
}
</style>
