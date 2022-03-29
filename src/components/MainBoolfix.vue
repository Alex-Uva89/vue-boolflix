<template>
  <main class="my-height bg-secondary">
      <div v-show="sendDataFilms == null && sendDataTv == null" class="text-center my-pt text-danger">
          <div class=" h1">
              Benvenuto in Boolfix
          </div> 
          <small class="text-white h3">
              inizia la ricerca
          </small>
      </div>
      <div v-show="sendDataFilms != null" class="text-white text-center text-uppercase py-5 h1">Movies</div>
      <div class="my-movies row row-cols-4 text-center">
        <div v-for="filmCard in sendDataFilms" 
        :key="filmCard.id" 
        class="my-card text-white col">
            <h2>{{ filmCard.title }}</h2>
            <h3>{{ filmCard.original_title }}</h3>
            <lang-flag :iso="filmCard.original_language" :squared="false" />
            <div>{{ filmCard.vote_average }}</div>
        </div>
      </div>
      <div v-show="sendDataTv != null" class="text-white text-center text-uppercase py-5 h1">Serie TV</div>
      <div class="my-tv  row row-cols-4 text-center">
        <div v-for="seriesCard in sendDataTv" 
        :key="seriesCard.id" 
        class="my-card text-white col">
            <h2>{{ seriesCard.name }}</h2>
            <h3>{{ seriesCard.original_name }}</h3>
            <lang-flag :iso="seriesCard.original_language" :squared="false" />
            <div>{{ seriesCard.vote_average }}</div>
        </div>
      </div>
  </main>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'MainBoolfix',
    components: {
        LangFlag
    },
    props: {
        sendDataFilms: Array,
        sendDataTv: Array
    }
}
</script>

<style lang="scss" scoped>
.my-height{
    min-height: calc(100vh - 5rem);
    .my-pt{
        padding-top: 15rem;
    }
}

</style>

// Milestone 1:
// Creare un layout base con una searchbar (una input e un button) in cui possiamo scrivere completamente o parzialmente il nome di un film. Possiamo, cliccando il  bottone, cercare sull’API tutti i film che contengono ciò che ha scritto l’utente.
// Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni film trovato: 
// Titolo
// Titolo Originale
// Lingua
// Voto

// Milestone 2:
// Trasformiamo la stringa statica della lingua in una vera e propria bandiera della nazione corrispondente, gestendo il caso in cui non abbiamo la bandiera della nazione ritornata dall’API (le flag non ci sono in FontAwesome).

// Milestone 3: TODO:
// In questa milestone come prima cosa aggiungiamo la copertina del film o della serie al nostro elenco. Ci viene passata dall’API solo la parte finale dell’URL, questo perché poi potremo generare da quella porzione di URL tante dimensioni diverse. 
