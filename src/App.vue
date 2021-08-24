<template>
  <div class="app">
    <AppHeader title="Anime Quotes Py"/>
    <Quote :quote="qoute"/>
    <div class="btn-container">
      <button @click="loadQuotes">Generate Qoute</button>
    </div>
    <QuoteHistory :quote="qoutes" />
  </div>
</template>

<script>
import AppHeader from './components/Header.vue'
import Quote from './components/Quote.vue'
export default {
  name: 'App',
  components: {
    AppHeader,
    Quote,
  },
  data () {
    return {
      qoute: {},
      qoutes: []
    }
  },
  methods: {
    async loadQuotes () {
      const data = await fetch("https://animechan.vercel.app/api/random").then(res => res.json());

      this.qoute = {
        content: data.quote,
        anime: data.anime,
        characters: data.character
      }
    }
  },

  created () {
    this.loadQuotes();
  }
}
</script>

<style lang="scss">
@import "./sass/main.scss";

.btn-container{
  display: flex;
  justify-content: center;
  padding: 0px 2rem;
  margin: 4rem auto;

  button{
    border: none;
    outline: none;
    background-color: get_color(primary);

    padding: 1rem 2rem;
    border-radius: 6rem;

    color: get_color(light);
    font-size: 1.5rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.1rem;
    cursor: pointer;
    transition: 0.5s;

    &:hover{
      background-color: get_color(secondary);
    }
  }
}

</style>
