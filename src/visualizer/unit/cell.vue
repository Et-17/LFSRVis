<script setup>
import { ref, watch } from 'vue'
defineProps({
    index: Number,
})

const state = ref(false);

// Toggle this cell's state
function toggle() {
    state.value = !state.value;
}

const cellsize = "50px";
const fontsize = "40px";
</script>

<template>
    <div class="cell" :class="{ active: state, inactive: !state }" @click="toggle">
        {{ index }}
    </div>
</template>

<style scoped>
.cell {
    width: v-bind(cellsize);
    height: v-bind(cellsize);
    line-height: v-bind(cellsize);
    font-size: v-bind(fontsize);
    font-family: monospace;
    text-align: center;
    border: 5px solid black;
    color: black;
}

.active {
    background-color: yellow;
}

.inactive {
    background-color: white;
}
</style>