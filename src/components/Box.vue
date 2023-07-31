<template>
    <div class="box ha-tex-weight-bold" :style="estilos">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { DefineComponent, defineComponent } from 'vue';

export default defineComponent({
    name: 'Box',
    data() {
        return {
            estilos: {
                backgroundColor: '#FAF0CA'
            }
        }
    }

})
</script>
