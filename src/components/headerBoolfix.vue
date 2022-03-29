<template>
  <div class="my-container bg-black d-flex align-items-center">
    <div class="container d-flex justify-content-between align-items-center">
      <h1 class="text-danger text-uppercase">Boolfix</h1>
      <form action="">
        <label for="input" class="text-white me-2">Cerca per titolo</label>
        <input type="text">
      </form>
    </div>
  </div>
</template>

<script>

export default {
    name:'HeaderBoolfix',
    data(){
      return {
        valueSearched: '',
      }
    }

}
</script>

<style lang="scss" scoped>
.my-container{
  height: 5rem;
}

</style>