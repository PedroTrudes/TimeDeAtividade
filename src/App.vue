<template>
  <!--Colocando uma classe se o modo escuro for True :class="{'modo-escuro': modoEscuroAtivo }"-->
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Forms @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <ListaTarefas v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <BoxMsg v-if="listaEstaVazia">
          Você não esta muito produtivo Hoje :/
        </BoxMsg>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Forms from './components/Forms.vue';
import ListaTarefas from './components/ListaTarefas.vue';
import ITarefa from './interface/ITarefa';
import BoxMsg from './components/BoxMsg.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Forms,
    ListaTarefas,
    BoxMsg
  },
  data(){
    return {
      tarefas: [] as ITarefa [],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaEstaVazia () : boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa (tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
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
