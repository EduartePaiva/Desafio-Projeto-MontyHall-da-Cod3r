<template>
    <!-- <img src="../imgs/presente.png" alt="" class="presente"> -->
    <div class="presente-emoji">🎁</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
})

</script>

<style lang="scss">
.presente{
    height: 80px;
    position: relative;
    top: 100%;
    left: 50%;
    transform: translate(-50%,-92%);
}

.presente-emoji{
    font-size: 70px;
    position: relative;
    top: 100%;
    left: 50%;
    transform: translate(-52%,-90%);
}
</style>