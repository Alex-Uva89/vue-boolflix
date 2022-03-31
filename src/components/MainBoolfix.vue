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
        <div class="my-movies text-center">
            <div v-for="filmCard in sendDataFilms" 
            :key="filmCard.id" 
            class="my-container-card">
                <div class="my-describe-card">
                    <h2>{{ filmCard.title }}</h2>
                    <small class="overview">
                    <p v-if="filmCard.overview == []" >Trama non trovata</p>
                    <p v-else> "{{filmCard.overview}}" </p>
                    </small>
                    <small>Titolo originale:</small>
                    <h4>{{ filmCard.original_title }}</h4>
                    <lang-flag :iso="filmCard.original_language" :squared="false" />
                    <div class="my-vote">
                    <span v-for="voto in 5" 
                    :key="voto.vote_average"
                     >
                     <i v-if="voto <= valoreVoto(filmCard.vote_average)" class="bi bi-star-fill"></i>
                     <i v-else class="bi bi-star"></i>
                     </span>
                    </div>
                </div>
                <div class="my-poster">
                    <div v-if="filmCard.poster_path == null" class="my-poster-img d-flex flex-column justify-content-center align-items-center">
                        <span class="text-uppercase text-danger">b</span>
                        <small>copertina non disponibile</small>
                    </div>
                    <img v-else :src="`${urlPoster}${filmCard.poster_path}`" :alt="filmCard.title +' pic'">
                </div>
            </div>
        </div>
      </div>
      <!-- .................... SERIES .....................  -->
      <div v-show="sendDataTv != null" class="text-white text-center text-uppercase py-5 h1">Serie TV</div>
      <div class="container pb-5">
        <div class="my-tv text-center">
            <div v-for="seriesCard in sendDataTv" 
            :key="seriesCard.id" 
            class="my-container-card">
                <div class="my-describe-card"></div>
                <h2>{{ seriesCard.name }}</h2>
                <small>Titolo originale:</small>
                <h3>{{ seriesCard.original_name }}</h3>
                <lang-flag :iso="seriesCard.original_language" :squared="false" />
                <div class="my-vote">
                    <span v-for="voto in 5" 
                    :key="voto.vote_average"
                     >
                     <i v-if="voto <= valoreVoto(seriesCard.vote_average)" class="bi bi-star-fill"></i>
                     <i v-else class="bi bi-star"></i>
                     </span>
                </div>

                <div class="my-poster">
                    <div v-if="seriesCard.poster_path == null" class="my-poster-img d-flex flex-column justify-content-center align-items-center">
                        <span class="text-uppercase text-danger">b</span>
                        <small>copertina non disponibile</small>
                    </div>
                    <img v-else :src="`${urlPoster}${seriesCard.poster_path}`" :alt="seriesCard.title +' pic'">
                </div>
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
    data(){
        return{
            urlPoster: 'https://image.tmdb.org/t/p/w342',
        }
    },
    props: {
        sendDataFilms: Array,
        sendDataTv: Array
    },
    methods: {
        valoreVoto(variabile){
            let result = Math.floor(variabile / 2)
           return result
        },
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

.my-movies,
.my-tv{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.my-container-card{
    color: white;
    width: 342px;
    height: 513px;
    margin: 10px;
    position: relative;
    
    &:hover{
        border: 1px solid white;
    }
    
    .overview{
        height: 20%;
        font-size: .7rem;
    }
    
}

.my-describe-card{
    width: 342px;
    max-height: 513px;
    padding: 1rem;
    opacity: 0%;
    transform: rotatey(-90deg);
    transition: transform 1s opacity 1s;;
}

.my-poster{
        position: absolute;
        top: 0;
        left: 0;
        transform: rotatey(0deg);
        transition: transform 1s;
        .my-poster-img{
        color: white;
        background: rgb(2,0,36);
        background: linear-gradient(45deg, rgba(0,0,0,1) 30%, rgba(245,37,9,1) 100%);
        width: 342px;
        height: 513px;
        padding: 2rem;
        border: 1px solid black;
        span{
            font-size: 10rem;
        }
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

Milestone 4: TODO:
// Trasformiamo quello che abbiamo fatto fino ad ora in una vera e propria webapp, creando un layout completo simil-Netflix:
// Un header che contiene logo e search bar
// Dopo aver ricercato qualcosa nella searchbar, i risultati appaiono sotto forma di “card” in cui lo sfondo è rappresentato dall’immagine di copertina (consiglio la poster_path con w342)
// Andando con il mouse sopra una card (on hover), appaiono le informazioni aggiuntive già prese nei punti precedenti più la overview
