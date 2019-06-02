<template>
<div>
  <section class="section">
    <div class="container">
      <h1 class="title">Valoraciones del producto</h1>
      <h2 class="subtitle">
        Aquí puedes consultar las últimas valoraciones que los usuarios han hecho sobre este producto.
      </h2>
    </div>
  </section>
  <section class="section">
    <div class="container">
      <div class="columns is-multiline">
        <AppValoracion
          v-for="(valoracion, index) in staticJson.reviews"
          v-bind:key="index"
          v-bind:valoracionData="valoracion" />
      </div>
    </div>
  </section>
  </div>
</template>

<script>
import axios from 'axios'
import AppValoracion from '@/components/AppValoracion.vue'
import reviewsData from '@/assets/reviews.json'

export default {
  name: 'home',
  components: {
    AppValoracion
  },
  data: function(){
    return{
      isLoaded: false,
      staticJson: reviewsData
    }
  },
  created(){
    
  },
  methods: {
    
  }

}
</script>
