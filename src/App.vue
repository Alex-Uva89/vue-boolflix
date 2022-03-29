<template>
  <div id="app">
    <header-boolfix
    @sendValue="searchTitle" />
    <main-boolfix
    :sendDataFilms="arrFilms"
    :sendDataTv="arrTv"
     />
    <!-- prima di partire a scrivere codice, preparo diagramma da seguire con United Diagrams -->
    
  </div>
</template>

<script>
import axios from 'axios';
import HeaderBoolfix from './components/headerBoolfix.vue';
import MainBoolfix from './components/MainBoolfix.vue';

export default {
  name: 'App',

  components: {
    HeaderBoolfix,
    MainBoolfix
    },

  data(){
    return {
      arrFilms: null,
      arrTv: null,
    }
  },

  methods: {
    searchTitle(value){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=d8713036d3f69ddd4290d81759004203&language=it-IT&query=${value}`)
      .then((responseFilm) => { this.arrFilms = responseFilm.data.results 
      console.log(responseFilm)
      }),
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=d8713036d3f69ddd4290d81759004203&language=it-IT&query=${value}`)
      .then((responseTv) => { this.arrTv = responseTv.data.results 
      console.log(responseTv)
      })
    }
  }
}
</script>

<style lang="scss">
$secondary: rgba(30,30,30,.2);

@import "~bootstrap/scss/bootstrap";
  // d8713036d3f69ddd4290d81759004203 API KEY

  html{
  }
</style>


// data:
// adult: false
// backdrop_path: "/rr7E0NoGKxvbkb89eR1GwfoYjpA.jpg"
// belongs_to_collection: null
// budget: 63000000
// genres: [{…}]
// homepage: "http://www.foxmovies.com/movies/fight-club"
// id: 550
// imdb_id: "tt0137523"
// original_language: "en"
// original_title: "Fight Club"
// overview: "Un uomo di trent'anni è insofferente su tutto e la notte non riesce più a dormire. In cerca di qualche luogo dove scaricare la propria ansia si mette a frequentare quei corsi dove gruppi di malati gravi si riuniscono e confessano agli altri le rispettive situazioni. Mentre si lascia andare alla commozione e al pianto di fronte a quello che vede, l'uomo fa la conoscenza prima di Marla Singer poi di Tyler Durden. Lei è una ragazza a sua volta alla deriva, incapace di scelte o decisioni; lui è un tipo deciso e vigoroso con un'idea precisa in testa. Tyler fa saltare per aria l'appartamento dell'uomo e i due vanno a vivere insieme in una casa fatiscente. Deciso a coinvolgerlo nel suo progetto, Tyler lo fa entrare in un 'Fight Club', uno stanzone sotterraneo dove ci si riunisce per picchiarsi e in questo modo sentirsi di nuovo vivi..."
// popularity: 72.085
// poster_path: "/rtNLQ8HbPElzEfrHjrzSr07prKT.jpg"
// production_companies: (6) [{…}, {…}, {…}, {…}, {…}, {…}]
// production_countries: (2) [{…}, {…}]
// release_date: "1999-10-15"
// revenue: 100853753
// runtime: 139
// spoken_languages: [{…}]
// status: "Released"
// tagline: "Combatti per sapere chi sei"
// title: "Fight Club"
// video: false
// vote_average: 8.4
// vote_count: 23748


