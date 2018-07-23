<template>
  <div id="app">
    <div class="principal">
      <p>Index: {{selectedShowEstado}}</p>
      <p>Estado: {{ selectedEstado }}</p>
      <div v-for="(estado,index) in optionsEstados" :key="index">
        <button @click="setSelectedEstado(estado,index)">{{estado}}</button>
        <cidade v-if="estado == selectedEstado" :items="optionsCidades" show="true" />
      </div>
    </div>
  </div>
</template>

<script>


import Cidade from './components/cidade.vue'

export default {
  name: 'app',

  components: {
    Cidade
  },

  data () {
    return {
      dados: [
        {
          estado: "AM",
          cidade: "Manaus",
          bairro: "Alvorada I",
          nome: "Nome 1"  
        },{
          estado: "AM",
          cidade: "Paritins",
          bairro: "Francesa",
          nome: "Nome 2"  
        },{
          estado: "PA",
          cidade: "Belem",
          bairro: "Centro",
          nome: "Nome 3"  
        },{
          estado: "PA",
          cidade: "Belem",
          bairro: "Kalipso",
          nome: "Nome 4"  
        },{
          estado: "RJ",
          cidade: "Rio Janeiro",
          bairro: "Cinelandia",
          nome: "Nome 5"  
        },{
          estado: "SP",
          cidade: "Sao Paulo",
          bairro: "Jardins",
          nome: "Nome 6"  
        },
      ],
      selectedEstado: "",
      selectedCidade: "",
      selectedBairro: "",
      selectedShowEstado: -1
    }
  },

  computed: {
    optionsEstados() {
      let estados = []
      this.dados.forEach( elem => {
        if ( estados.indexOf(elem.estado) == -1 ) {
          estados.push(elem.estado)
        }
      })
      return estados
    },
    optionsCidades() {
      let cidades = []
      this.dados.forEach( elem => {
        if (elem.estado == this.selectedEstado) {
          if (cidades.indexOf(elem.cidade) == -1 ) {
            cidades.push(elem.cidade)
          }
        }
      })
      return cidades
    }
  },

  methods: {
    setSelectedEstado(vuf,vindex) {
      this.selectedEstado = vuf 
      this.selectedShowEstado = vindex
    }
  }


}
</script>

<style scoped>

  .principal {
    background-color: gray;
    top: 20px;
    width: 80%;
    height: 80%;
    margin-left: 10%;
  }

</style>
