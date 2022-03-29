<template>
  <main class="my-main bg-secondary">
      <div class="container">
        <div v-for="filmCard in sendDataFilms" 
        :key="filmCard.id" 
        class="my-card text-white">
            <h2>{{ filmCard.title }}</h2>
            <h3>{{ filmCard.original_title }}</h3>
            <h4>{{ filmCard.original_language }}</h4>
            <div>{{ filmCard.vote_average }}</div>
        </div>
      </div>
  </main>
</template>

<script>
export default {
    name: 'MainBoolfix',
    props: {
        sendDataFilms: Object,
    }
}
</script>

<style lang="scss" scoped>
.my-main{
    height: calc(100vh - 5rem);
}

</style>

// Milestone 1:
// Creare un layout base con una searchbar (una input e un button) in cui possiamo scrivere completamente o parzialmente il nome di un film. Possiamo, cliccando il  bottone, cercare sull’API tutti i film che contengono ciò che ha scritto l’utente.
// Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni film trovato: 
// Titolo
// Titolo Originale
// Lingua
// Voto
