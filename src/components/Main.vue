<template>
  <div>
    <div class="d-flex flex-wrap justify-content-center">
      <Single 
        :image="pokemonItem.sprites.other.dream_world.front_default"
        :name="pokemonItem.name"
        :type="pokemonItem.types[0].type.name"
      />
    </div>
  </div>
</template>
<script>
import Single from "./Single.vue";

export default {
  name: "Main",
  components: {
    Single
  },
  props: {
    pokemonItem: Object
  }
};
</script>
