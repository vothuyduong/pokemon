<script setup>
import CardFlip from "./Card.vue"

defineProps({
    cardsContext: {
        type: Array,
        default: []
    }
})
</script>

<template>
    <div class="scre">
        <h1>Interact Component here...</h1>
        <CardFlip v-for="(card, index) in cardsContext" :key="index" :imgBackFaceUrl="`images/${card}.png`"/>
    </div>
</template>