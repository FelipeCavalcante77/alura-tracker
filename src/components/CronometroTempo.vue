<template>
       <section>
            <strong class="display-4">
                {{ tempoFormatado }}
            </strong>
        </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'CronometroTempo',
    props: {
        tempoEmSegundos: {
            type: Number,
            required: true
        }
    },
    computed: {
        tempoFormatado() : string {
          return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
        }
    }

});
</script>

<style scoped>
    .display-4 {
        font-size: 2.5rem;
        font-weight: bold;
        color: var(--destaque-forte);
        letter-spacing: 0.04em;
        font-variant-numeric: tabular-nums;
    }
</style>
