<!-- <script setup>
const props = defineProps({
    msg: String
})
</script>

<template>
    <h2>{{ msg || 'Реквізит ще не переданий' }}</h2>
</template> -->


<!--випромінювання події батьківському компоненту -->
<script setup>
const emit = defineEmits(['response'])

emit('response', 'привіт від дочі')
</script>

<template>
    <h2>Дочірній компонент</h2>
</template>