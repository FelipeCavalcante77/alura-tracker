<template>
    <button class="button is-danger" @click="pararContador" :disabled="!cronometroRodando">
        <span class="icon"><i class="fas fa-stop"></i></span> Parar
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'BotaoParar',
    emits: ['aoPararContador'],
    props: {
        cronometroRodando: {
            type: Boolean,
            required: true
        }
    },
    methods: {
        pararContador() {
            this.$emit('aoPararContador');
            
        }
        
    }
});
</script>