<template>
  <section>
    <h2>Search for a Joke</h2>

    <audio src="./laughing.mp3" autoplay></audio>
    
    <form @submit.prevent="handleSubmit">
      <input v-model="keyword" required>
      <button class="search-button">Search</button>
    </form>
    
  </section>
</template>

<script>

export default {
  props: {
    search: String,
    onSearch: Function
  },
  data() {
    return {
      keyword: this.search || ''
    };
  },
  watch: {
    search(newSearch) {
      if(this.keyword !== newSearch) {
        this.keyword = newSearch;
      }
    }
  },
  methods: {
    handleSubmit() {
      this.$router.push({
        query: {
          search: encodeURIComponent(this.keyword)
        }
      });
    }
  }
};
</script>

<style>

input {
  margin-right: 10px;
}

.search-button {
  margin-bottom: 30px;
}

</style>
