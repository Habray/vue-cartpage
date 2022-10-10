<script setup>

</script>

<template>
    <h3><slot name="default"/></h3>
    <p v-if="$slots.paragraph"><slot name="paragraph"/></p>

</template>