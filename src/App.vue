<template>
  <main class="columns is-gapless is-multiline"  :class="{ 'modo-escuro':modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class=" column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <Box v-if ="listaEstaVazia">
          Voce não está produtivo hoje:(
       </Box>
     </div>
     
    </div>
  </main>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import BarraLateral from './components/BarraLareral.vue'
import Formulario from './components/Formulario.vue'
import Tarefa from './components/Tarefa.vue'
import ITarefa from './interfaces/ITarefa'
import Box from './components/Box.vue'
// import Tarefa from './'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo:false
    }
  },
  computed:{
    listaEstaVazia() : boolean{
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista {
   padding: 1.25rem;
}

main{
  --bg-primario:#d1dbe983;
  --texto-primario:#000;
  
}
main.modo-escuro{
  --bg-primario:#252527;
  --texto-primario:#f3f0f0;
  
}

.conteudo{
  background-color: var(--bg-primario);
}
</style>
