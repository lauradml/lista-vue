<template>
  <div class="home">
    <Listado/>
  </div>
</template>

<script>
// @ is an alias to /src
import Listado from '@/components/Listado.vue'

export default {
  name: 'home',
  components: {
    Listado
  }
}
</script>

<style lang = "css" >
.home {
 display: flex;
 justify-content: center;
}
</style>
