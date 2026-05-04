<template>
   <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario de cadastro de tarefa">
                <p class="tag-formulario">Nova tarefa</p>
                <h2 class="titulo-formulario">Planeje o proximo bloco de foco</h2>

                <div class="field">

                    <label class="label" for="titulo">Titulo</label>
                    
                    <div class="control">
                        <input class="input" type="text" id="titulo" placeholder="Titulo da tarefa" v-model="titulo" required>
                    </div>

                    <div class="column cronometro-area">

                      <TemporizadorCronometro @ao-temporizador-finalizado="finalizarTarefa"/>


                    </div>
                

                </div>

            </div>
        </div>
   </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorCronometro from './TemporizadorCronometro.vue';

export default defineComponent({
    name: 'FormularioTempo',
    emits: ['aoSalvarTarefa'],
    components: {
        TemporizadorCronometro
    },
    data (){
        return {
            titulo: ''
        }
    },
    methods: {
        finalizarTarefa(tempoEmSegundos: number) : void {
            this.$emit('aoSalvarTarefa', {
                titulo: this.titulo,
                tempoEmSegundos: tempoEmSegundos
            });
            this.titulo = '';
        }
    }

});
</script>


<style>
    .formulario {
      color: var(--texto-primary);
      background: var(--bg-card);
      border: 1px solid var(--borda-suave);
      border-radius: 28px;
      padding: 1.5rem;
      box-shadow: var(--sombra-card);
      backdrop-filter: blur(12px);
    }

    .tag-formulario {
      margin: 0 0 0.5rem;
      font-size: 0.78rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--destaque);
    }

    .titulo-formulario {
      margin: 0 0 1.5rem;
      font-size: 2rem;
      line-height: 1.1;
      color: var(--texto-primary);
    }

    .label {
      color: var(--texto-primary);
      font-weight: 700;
    }

    .input {
      min-height: 3.5rem;
      border-radius: 18px;
      border: 1px solid var(--borda-suave);
      background: var(--bg-card-strong);
      box-shadow: none;
      color: var(--texto-primary);
    }

    .input::placeholder {
      color: var(--texto-soft);
    }

    .input:focus {
      border-color: var(--destaque);
      box-shadow: 0 0 0 0.2rem rgba(217, 119, 87, 0.15);
    }

    .cronometro-area {
      padding-left: 0;
    }
</style>
