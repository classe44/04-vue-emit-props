<template>
  <div>
    <input
      type="text"
      placeholder="cerca un pokemon"
      class="form-control"
      v-model="searchText"
    />
    <input
      type="button"
      value="Cerca"
      class="btn btn-primary ml-2"
      @click="search"
    />
    <div>
      (es. bulbasaur, ivysaur, venusaur, charmander, charmeleon, charizard)
    </div>
  </div>
</template>
<script>
export default {
  name: "Header",
  data() {
    return {
      searchText: ""
    };
  },
  methods: {
    search() {
        console.log('Header.vue sta facendo partire un evento', this.searchText);
        this.$emit('newSearch', this.searchText);
    }
  }
};
</script>
