<template>

  <header class="my-container bg-black d-flex align-items-center">
    <div class="container d-flex justify-content-between align-items-center">
      <h1 class="text-danger container-logo">
        <span class="text-animation">
          Boolfix
        </span> 
      </h1>
      <div>
        <label for="input" class="text-white me-2">Cerca per titolo</label>
        <input type="text" v-model="requiredValue" @keyup.enter="$emit('sendValue', requiredValue)">
      </div>
    </div>
  </header>
</template>

<script>

export default {
    name:'HeaderBoolfix',
    data(){
      return {
        requiredValue: '',
      }
    },
    methods: {

    }
    

}
</script>

<style lang="scss" scoped>
.my-container{
  height: 5rem;
}
.container-logo{
  position: relative;
}

.text-animation{
  -webkit-mask-image: radial-gradient(circle, black 20%, rgba(0, 0, 0, 0.5) 60%);
  mask-image: radial-gradient(circle, black 80%, rgba(0, 0, 0, 0.5) 20%);

  animation-name: text-color;
  animation-duration: 6s;
  animation-iteration-count: infinite;
}

@keyframes text-color {
  
}

</style>