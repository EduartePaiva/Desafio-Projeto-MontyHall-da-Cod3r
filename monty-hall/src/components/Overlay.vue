<template>
    <div class="overlay">
        <div class="texto">
            {{ mensagemOverlay }}
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    props: {
        mensagemOverlay:String
    }
})
</script>

<style lang="scss" scoped>
.overlay {
    position: fixed;
    /* Sit on top of the page content */
    display: block;
    /* Hidden by default */
    width: 100%;
    /* Full width (cover the whole page) */
    height: 100%;
    /* Full height (cover the whole page) */
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    /* Black background with opacity */
    z-index: 2;
    /* Specify a stack order in case you're using a different order for other elements */
    cursor: pointer;
    /* Add a pointer on hover */

    .texto {
        position: absolute;
        top: 50%;
        left: 50%;
        font-size: 50px;
        color: white;
        transform: translate(-50%, -50%);
        -ms-transform: translate(-50%, -50%);
        text-align: center;
    }
}</style>