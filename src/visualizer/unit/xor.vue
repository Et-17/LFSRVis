<script setup>
import { ref } from 'vue'
defineProps({
    first_arg: Boolean,
    second_arg: Boolean,
})

const activated = ref(false);

const diameter = "40px"; // The normal diameter
const rollover_dia = "50px"; // The diameter when the user mouses over
</script>

<template>
    <div class="xor-gate">

    </div>
</template>

<style scoped>
.xor-gate {
    width: v-bind(diameter);
    height: v-bind(diameter);
    border: 1px solid black;
    border-radius: 100%;
    transform-origin: center;
    background-color: white;
}

.xor-gate:hover {
    width: v-bind(rollover_dia);
    height: v-bind(rollover_dia);
}
</style>