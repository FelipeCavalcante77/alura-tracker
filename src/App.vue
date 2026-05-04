<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter painel-lateral">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>

    <div class="column is-three-quarter conteudo">
      <FormularioTempo @aoSalvarTarefa="salvarTarefa" />

      <div class="lista">
        <TarefaLista v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />

        <BoxLayout v-if="listaEstaVazia">
          Voce nao esta muito produtivo hoje? Que tal dar uma pausa para um cafe e depois voltar com tudo para as suas tarefas?
        </BoxLayout>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTempo from './components/FormularioTempo.vue';
import TarefaLista from './components/TarefaLista.vue';
import Itarefa from './interfaces/ITarefa';
import BoxLayout from './components/BoxLayout.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTempo,
    TarefaLista,
    BoxLayout
  },
  data () {
    return {
      tarefas: [] as Itarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: Itarefa) : void {
      this.tarefas.push(tarefa);
    },
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo;
    }
  }
});
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;700&display=swap');

  * {
    box-sizing: border-box;
  }

  body {
    margin: 0;
    font-family: 'Outfit', sans-serif;
    background: #f5efe6;
  }

  .lista {
    margin-top: 1.5rem;
  }

  main {
    --bg-primary: #f7f1e8;
    --bg-card: rgba(255, 250, 244, 0.82);
    --bg-card-strong: #fffdf8;
    --texto-primary: #2f241f;
    --texto-soft: #6b5a50;
    --borda-suave: rgba(123, 92, 74, 0.14);
    --destaque: #d97757;
    --destaque-forte: #bc5f43;
    --sombra-card: 0 18px 45px rgba(92, 60, 39, 0.12);
    min-height: 100vh;
    background:
      radial-gradient(circle at top left, rgba(240, 181, 145, 0.45), transparent 30%),
      radial-gradient(circle at bottom right, rgba(214, 150, 111, 0.22), transparent 28%),
      var(--bg-primary);
    transition: background-color 0.3s ease, color 0.3s ease;
  }

  main.modo-escuro {
    --bg-primary: #1a1412;
    --bg-card: rgba(49, 39, 35, 0.8);
    --bg-card-strong: #2a211e;
    --texto-primary: #f6ede4;
    --texto-soft: #cfb9aa;
    --borda-suave: rgba(246, 237, 228, 0.12);
    --destaque: #ff9a6c;
    --destaque-forte: #ffc7a4;
    --sombra-card: 0 18px 45px rgba(0, 0, 0, 0.35);
  }

  .painel-lateral {
    display: flex;
  }

  .conteudo {
    background-color: transparent;
    color: var(--texto-primary);
    min-height: 100vh;
    padding: 3rem;
  }

  @media only screen and (max-width: 768px) {
    .conteudo {
      padding: 1.5rem;
    }
  }
</style>
