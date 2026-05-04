<template>
    <button class="button is-primary" @click="iniciarContador" :disabled="cronometroRodando">
        <span class="icon"><i class="fas fa-play"></i></span> Iniciar
    </button>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'BotaoIniciar',
    emits: ['aoIniciarContador'],
    props: {
        cronometroRodando: {
            type: Boolean,
            required: true
        }
    },
    methods: {
       iniciarContador() {
            this.$emit('aoIniciarContador');
        }
    }
});
</script>