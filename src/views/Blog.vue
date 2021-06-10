<template>
  <Titulo texto="Título de mi Blog"/>
  <button class="btn btn-primary" @click="consumirApi">Consumir Api</button>

  <div class="mt-3" v-for="item in arrayBlog" :key="item.id">
    <div class="card">
      <router-link :to="`/blog/${item.id}`">
        {{ item.title }}
      </router-link>
    </div>
  </div>
</template>

<script>
import Titulo from '../components/Titulo'
export default {
    components: {
        Titulo,
    },
    data() {
      return {
        arrayBlog: []
      }
    },
    methods: {
      async consumirApi(){
        try {
          const data = await fetch('https://jsonplaceholder.typicode.com/posts')
          const array = await data.json()
          //console.log(array)
          this.arrayBlog = array
        } catch (error) {
          console.log(error)
        }
      }
    },
    created() {
      this.consumirApi()
    }

}
</script>

<style>

</style>