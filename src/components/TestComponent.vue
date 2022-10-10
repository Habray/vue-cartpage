<script setup>
    defineProps({
        testProps: {
            type: String,
            required: true,
        }
    })
</script>
<template>
    <h6>This is a test component for props {{testProps}}</h6>
</template>