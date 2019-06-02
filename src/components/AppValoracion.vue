<template>
<div class="column is-12-mobile is-half-tablet is-4-desktop">
    <div class="valoracion">
        <div class="estrellas">
            <span 
                class="icon iconStar"
                v-for="(n, index) in 5"
                v-bind:key="index">
                  <i class="far fa-star" v-bind:class="{'fas fa-star': n<valoracionData.rating}"></i>                  
                </span>
        </div>
        <div class="autor">
            <span class="ultimaValoracion">
                  {{valoracionData.author}} el {{moment(valoracionData.date).format('DD')}} de {{moment(valoracionData.date).format('MMM')}} de {{moment(valoracionData.date).format('YYYY')}}
                </span>
        </div>
        <div class="comentario">
            <span class="ultimoComentario">
                  {{valoracionData.comment}}
                </span>
        </div>
        <div class="boton-util">
            <a class="button"
              :disabled="isUtil"
              v-bind:class="{'btn-pulsado-es-util': isUtil}"
              v-on:click="votaEsUtil()">
                <span class="icon is-small">
                <i class="fas fa-thumbs-up"></i>
                </span>
                <span>Es útil</span>
            </a>
            <span class="esutil"> {{totalUtil}} {{mensajeUtil}} </span>
        </div>
    </div>
</div>
</template>
<script>


export default {
  name: 'AppValoracion',
  props: ['valoracionData'],
  data: function(){
    return{
      isLoaded: false,
      isUtil: false,
      mensajeUtil: "personas creen que es útil",
      totalUtil: this.valoracionData.useful_count
    }
  },
  methods:{
    votaEsUtil(){
        if(!this.isUtil){
            this.isUtil = true;
            this.totalUtil++;
            this.mensajeUtil = "personas creéis que es útil"
        }
    }
  },
  mounted(){
    
  }
};
</script>
<style lang="scss" scoped>
.valoracion {
    border:solid 1px gray;
    -webkit-border-radius: 6px;
    -moz-border-radius: 6px;
    border-radius: 6px;
    padding: 10px;

    .estrellas, .boton-util{
        width:100%;
    }
    .autor, .comentario{
        width:100%;
        margin: 10px 0 10px 0;
    }
    
}
.iconStar {
            color:#dec60f;
        }
.btn-pulsado-es-util{
    background-color:green;
    color:white;
}
.esutil{
    margin-left: 10px;
    margin-top:6px;
}
.ultimaValoracion {
    color: gray;
}
.ultimoComentario {
    font-weight: 600;
}
</style>