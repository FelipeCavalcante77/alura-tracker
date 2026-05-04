<template>
    <div class="box has-text-weight-bold" :style="estilos">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BoxLayout',
    data() {
        return {
            estilos: {
                background: 'var(--bg-card)',
                border: '1px solid var(--borda-suave)',
                borderRadius: '24px',
                padding: '1.2rem 1.3rem',
                marginBottom: '1rem',
                boxShadow: 'var(--sombra-card)',
                color: 'var(--texto-primary)',
                backdropFilter: 'blur(10px)'
            }
        }
    }
});
</script>

