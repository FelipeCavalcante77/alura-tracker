<template>
    <BoxLayout>
        <div class="columns is-vcentered tarefa-card">
            <div class="column is-8">
                <p class="etiqueta">Em andamento</p>
                <p class="is-size-4 titulo-tarefa">{{ tarefa.titulo || 'Titulo nao definido' }}</p>
            </div>
            <div class="column is-4 tempo-coluna">
                <CronometroTempo :tempoEmSegundos="tarefa.tempoEmSegundos" />
            </div>
        </div>
    </BoxLayout>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroTempo from './CronometroTempo.vue';
import ITarefa from '../interfaces/ITarefa';
import BoxLayout from './BoxLayout.vue';

export default defineComponent({
    name: 'TarefaLista',
    components: {
        CronometroTempo,
        BoxLayout
    },
    props: {
       tarefa:{
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
});

</script>

<style scoped>
    .tarefa-card {
        align-items: center;
    }

    .etiqueta {
        margin: 0 0 0.35rem;
        text-transform: uppercase;
        letter-spacing: 0.1em;
        font-size: 0.72rem;
        font-weight: 700;
        color: var(--destaque);
    }

    .titulo-tarefa {
        margin: 0;
        color: var(--texto-primary);
    }

    .tempo-coluna {
        display: flex;
        justify-content: flex-end;
    }

    @media only screen and (max-width: 768px) {
        .tempo-coluna {
            justify-content: flex-start;
        }
    }
</style>
