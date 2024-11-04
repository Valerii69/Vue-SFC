<!-- <script setup>
const props = defineProps({
    msg: String
})
</script>

<template>
    <h2>{{ msg || 'Реквізит ще не переданий' }}</h2>
</template> -->


<!--випромінювання події батьківському компоненту -->
<!-- <script setup>
const emit = defineEmits(['response'])

emit('response', 'привіт від дочі')
</script>

<template>
    <h2>Дочірній компонент</h2>
</template> -->

<!-- Слоти -->
<!-- <template>
    <slot>Запасний контент</slot>
</template> -->


<!--
      Ми надаємо кожному елементу завдання об'єкт todo,
      який він представляє, щоб його вміст був динамічним.
      Нам також потрібно надати кожному компоненту ключ
      "key", який пояснюється в розділі посібника про v-for.
    -->
<script setup>
const props = defineProps({
    todo: Object
})
</script>

<template>
    <li>{{ todo.text }}</li>
</template>