<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between temporizador">
        <section>
            <strong><CronometroTempo :tempoEmSegundos="tempoEmSegundos" /></strong>
        </section>

        <BotaoIniciar @aoIniciarContador="iniciarContador" :cronometroRodando="cronometroRodando" />

        <BotaoParar @aoPararContador="pararContador" :cronometroRodando="cronometroRodando" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTempo from './CronometroTempo.vue';
import BotaoIniciar from './BotaoIniciar.vue';
import BotaoParar from './BotaoParar.vue';

export default defineComponent({
    name: 'TemporizadorCronometro',
    emits: ['aoTemporizadorFinalizado'],
    components: {
        CronometroTempo,
        BotaoIniciar,
        BotaoParar
    },
    data() {
        return {
            cronometro: 0,
            tempoEmSegundos: 0,
            cronometroRodando: false,
            
        }
    },
    methods: {
        iniciarContador() {
            this.cronometroRodando = true;
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos++;
            }, 1000);
        },
        pararContador() {
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.cronometro = 0;

            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;

        }
    }
});

</script>

<style scoped>
    .temporizador {
        gap: 1rem;
        flex-wrap: wrap;
        margin-top: 1rem;
        padding: 1rem 1.1rem;
        border-radius: 22px;
        background: var(--bg-card-strong);
        border: 1px solid var(--borda-suave);
    }
</style>
