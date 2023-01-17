<script setup>
import { ref, watch } from 'vue'
defineProps({
    index: Number,
    size: String,
    border: String,
})

const state = ref(false);

// Toggle this cell's state
function toggle() {
    state.value = !state.value;
}

const fontsize = "40px";
</script>

<template>
    <div class="cell" :class="{ active: state, inactive: !state }" @click="toggle">
        {{ index }}
    </div>
</template>

<style scoped>
.cell {
    width: calc(v-bind(size) - calc(v-bind(border) * 2));
    height: calc(v-bind(size) - calc(v-bind(border) * 2));
    line-height: calc(v-bind(size) - calc(v-bind(border) * 2));
    font-size: v-bind(fontsize);
    font-family: monospace;
    text-align: center;
    border: v-bind(border);
    border-style: solid;
    border-color: black;
    color: black;
}

.active {
    background-color: yellow;
}

.inactive {
    background-color: white;
}
</style>