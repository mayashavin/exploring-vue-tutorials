<template>
  <div class="home">
    <pokemon-card />
  </div>
</template>

<script>
// @ is an alias to /src
import PokemonCard from '@/components/PokemonCard.vue';

export default {
  name: 'home',
  components: {
    PokemonCard,
  },
};
</script>