<template>
    <BoxMsg>
        <div class="columns">
            <div class="column is-7">
                {{tarefa?.descricao || 'Tarefa sem Descrição'}}
            </div>
            <div class="column">
                <Cronometro :tempoEmSegundos="tarefa?.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxMsg>
</template>

<script lang="ts">
import ITarefa from '@/interface/ITarefa';
import {defineComponent, PropType} from 'vue';
import Cronometro from './Cronometro.vue';
import BoxMsg from './BoxMsg.vue';

export default defineComponent({
    name: 'ListaTarefa',
    components:{
        Cronometro,
        BoxMsg,
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            require: true
        }
    }
})

</script>

<style scoped>
.box{
   
}
</style>