<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
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
      tarefas: [] as ITarefa []
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
    }
  }
});
</script>

<style scoped>
.lista{
  padding: 2em;
}
</style>
