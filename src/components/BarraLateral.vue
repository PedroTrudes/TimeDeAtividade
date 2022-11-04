<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="Logo da aplicação">
        </h1>
        <div class="has-text-centered">
          <button class="button" @click="alterarTema">
              {{textoBotao}}
          </button>
        </div>
        <nav class="panel mt-5 p-5">
            <ul>
              <li>
                <router-link to="/" class="link">
                  <i class="fas fa-task">
                    Tarefas
                  </i>
                </router-link>
              </li>
              <li>
                <router-link to="/projetos" class="link">
                  <i class="fas fa-project-diagram">
                    Projetos
                  </i>

                </router-link>
              </li>
            </ul>
        </nav>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';


export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data (){
      return{
        modoEscuroAtivado: false
      }
    },
    computed: {
      textoBotao (){
        if(this.modoEscuroAtivado){
          return 'Desativar modo escuro'
        }
        return 'Ativar modo escuro'
      }
    },
    methods: {
      alterarTema() {
        this.modoEscuroAtivado = !this.modoEscuroAtivado
        this.$emit('aoTemaAlterado', this.modoEscuroAtivado )
      }
    }
})
</script>


<style scoped>
/* Todo o estilo do componente */
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}
header h1{
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
.panel li {
    margin: 8px 0;
    
}
.link {
    color: #fff;
}
.link:hover {
    color: #FAF0CA;
}
.link.router-link-active {
    color: #FAF0CA;
}
</style>