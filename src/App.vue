<template>
  <div class = "app">
    <header>
      <h2>ani<strong>SEARCH</strong></h2>

      <form class = "search-box" @submit.prevent = "handleSearch">
        <input 
          type="search"  
          class = "search-field"  
          placeholder = "Search for an Anime..."
          required 
          v-model = "search_query"/>
      </form>

    </header>

    <main>
      <div class = "cards">
        <Card/>
      </div>
    </main>

    

  </div>
</template>

<script>
import Card from './components/Card.vue';
import { ref } from "vue";

export default {

  components: {
    Card
  },
  setup() {
    const search_query = ref("");
    const animeList = ref([]);
    const handleSearch = async () => {
      animeList.value = await fetch (`https://api.jikan.moe/v4/anime/${search_query.value}/full`)
        .then(res => res.json())
        .then(data => data.results);
      console.log(animeList.value);
    }

    return {
      Card,
      search_query,
      animeList,
      handleSearch
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');

 * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", "sans-serif";
 }
 a {
  text-decoration: none;
 }
 header {
  padding-top: 50px;
  padding-bottom: 50px;
  h2 {
    color: #888;
    font-size: 42px;
    text-align: center;
    transition: 0.4s;
    margin-bottom: 30px;

    strong {
      color: #000;
    }
    &:hover {
      color: #313131;
      letter-spacing: 2px;
    }
  }
  .search-box {
    display: flex;
    justify-content: center;
    padding-left: 30px;
    padding-right: 30px;
    .search-field {
      appearance: none;
      background: none;
      border: none;
      outline: none;

      background-color: #f3f3f3;
      display: block;
      width: 100%;
      max-width: 600px;
      padding: 15px;
      border-radius: 15px;

      color: #313131;
      transition: 0.4s;

      &::placeholder {
        color: #aaa;
      }
      &:focus, &:valid {
        color: #fff;
        background-color: #313131;
      }
    }
  }
 }
 main {
  max-width: 1200px;
  margin: 0 auto;
  padding-left: 30px;
  padding-right: 30px;
  .card {
    display: flex;
    flex-wrap: wrap;
    margin: 0 -8px;
  }
 }

</style>
