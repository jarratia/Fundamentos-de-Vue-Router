<template>
  <Titulo texto="Artículos" />
  <h3 class="mt-3">{{ articulo.title }}</h3>
  <p>{{ articulo.body }}</p>
</template>

<script>
import Titulo from '../components/Titulo'

export default {
    components: {
        Titulo,
    },
    data() {
      return {
        articulo: []
      }
    },
    methods: {
      async consumirArticulo(){
        try {
          const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
          const object = await data.json()
          //console.log(array)
          this.articulo = object
        } catch (error) {
          console.log(error)
        }
      }
    },
    created() {
      this.consumirArticulo()
    }
}
</script>

<style>

</style>

