<script setup>
import { ref } from 'vue'
import cell from './cell.vue'
import xor from './xor.vue'
defineProps({
    index: Number,
})

const xor_args = [false, false];

// The length of the cable between cells
const inter_cell_distance = "100px";
// The length of the vertical cable
const vertical_distance = "200px";
// The thickness of the cables
const thickness = "5px";
// The color of cables
const cable_color = "black";
// The size of the cells
const cell_size = "50px";
// The border thickness of the cells
const cell_border = "8px";
</script>

<template>
    <div class="unit">
        <cell class="cell-block" :index="index" :size="cell_size" :border="cell_border" />
        <div class="horizontal"></div>
        <div class="vertical"></div>
        <xor :first_arg="xor_args[0]" :second_arg="xor_args[1]" class="xor-gate" />
    </div>
</template>

<style scoped>
.unit {
    position: relative;
    height: calc(v-bind(vertical_distance) + calc(v-bind(cell_size) / 2));
    width: calc(v-bind(cell_size) + v-bind(inter_cell_distance));
}

.cell-block {
    position: absolute;
    left: 0px;
    transform-origin: bottom left;
    top: calc(100% - v-bind(cell_size));
}

.horizontal {
    position: absolute;
    height: v-bind(thickness);
    width: v-bind(inter_cell_distance);
    background-color: v-bind(cable_color);
    right: 0px;
    top: calc(v-bind(vertical_distance) - calc(v-bind(thickness) / 2));
}

.vertical {
    position: absolute;
    height: v-bind(vertical_distance);
    width: v-bind(thickness);
    background-color: v-bind(cable_color);
    right: calc(calc(v-bind(inter_cell_distance) / 2) + calc(v-bind(thickness) / 2));
}

.xor-gate {
    position: absolute;
    right: calc(calc(v-bind(inter_cell_distance) / 2) + calc(v-bind(thickness)));
    top: v-bind(vertical_distance);
    transform: translate(50%, -50%);
}
</style>