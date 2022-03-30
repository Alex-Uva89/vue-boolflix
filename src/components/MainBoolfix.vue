<template>
  <main class="my-height bg-secondary">
      <!-- ................ WELCOME MESSAGE ................  -->
      <div v-show="sendDataFilms == null && sendDataTv == null" class="text-center my-pt text-danger">
          <div class=" h1">
              Benvenuto in Boolfix
          </div> 
          <small class="text-white h3">
              inizia la ricerca
          </small>
      </div>
      <!-- .................... MOVIE ...................... -->
      <div v-show="sendDataFilms != null" class="text-white text-center text-uppercase py-5 h1">Movies</div>
      <div class="container">
        <div class="my-movies row row-cols-2 row-cols-md-3 row-cols-lg-4 text-center">
            <div v-for="filmCard in sendDataFilms" 
            :key="filmCard.id" 
            class="my-card text-white col border border-white">
                <h2>{{ filmCard.title }}</h2>
                <h3>{{ filmCard.original_title }}</h3>
                <lang-flag :iso="filmCard.original_language" :squared="false" />
                <div>{{ funzioneVoto(filmCard.vote_average) }}</div>
            </div>
        </div>
      </div>
      <!-- .................... SERIES .....................  -->
      <div v-show="sendDataTv != null" class="text-white text-center text-uppercase py-5 h1">Serie TV</div>
      <div class="container pb-5">
        <div class="my-tv row  row row-cols-2 row-cols-md-3 row-cols-lg-4 text-center">
            <div v-for="seriesCard in sendDataTv" 
            :key="seriesCard.id" 
            class="my-card text-white col border border-white">
                <h2>{{ seriesCard.name }}</h2>
                <h3>{{ seriesCard.original_name }}</h3>
                <lang-flag :iso="seriesCard.original_language" :squared="false" />
                <div>{{ seriesCard.vote_average }}</div>
            </div>
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
    },
    methods: {
        funzioneVoto(variabile){
            let result = ''
            switch (Math.floor(variabile / 2)) {
                    case 1:
                        result = '!'
                        break;
                    case 2:
                        result = '!!'
                        break;
                    case 3:
                        result = '!!!'
                        break;
                    case 4:
                        result = '!!!!'
                        break;
                    case 5:
                        result = '!!!!!'
                        break;
                
                    default:
                        break;
                }
           return result
        }
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

.my-card{
    padding: 2rem;
    height: 300px;
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

Milestone 4: TODO:
// Trasformiamo quello che abbiamo fatto fino ad ora in una vera e propria webapp, creando un layout completo simil-Netflix:
// Un header che contiene logo e search bar
// Dopo aver ricercato qualcosa nella searchbar, i risultati appaiono sotto forma di “card” in cui lo sfondo è rappresentato dall’immagine di copertina (consiglio la poster_path con w342)
// Andando con il mouse sopra una card (on hover), appaiono le informazioni aggiuntive già prese nei punti precedenti più la overview
