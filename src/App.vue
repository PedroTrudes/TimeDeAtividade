<template>
  <!--Colocando uma classe se o modo escuro for True :class="{'modo-escuro': modoEscuroAtivo }"-->
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <!--Aqui vai a view correspondente com a rota-->
      <RouterView ></RouterView>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';


export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
  
  },
  data(){
    return {
      modoEscuroAtivo: false
    }
  },
  methods: {
    trocarTema (modoEscuroAtivado: boolean){
      this.modoEscuroAtivo = modoEscuroAtivado
    }
  }
});
</script>

<style scoped>
.lista{
  padding: 2em;
}
main{
 --bg-primario: #fff;
 --texto-primario: #000;

}
main.modo-escuro {
  --bg-primario: #2b2d42;
 --texto-primario: #ddd;
}

.conteudo{
  background-color: var(--bg-primario);
}
</style>
