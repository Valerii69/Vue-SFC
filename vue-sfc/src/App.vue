<!-- Обчислювані властивості -->

<!-- <script setup>
import { ref, computed } from 'vue'

// надай кожному завданню унікальний id
let id = 0

const newTodo = ref('')
const styleButton = ref("button")
const hideCompleted = ref(false)

const todos = ref([
  { id: id++, text: 'Вивчити HTML', done: true },
  { id: id++, text: 'Вивчити JavaScript', done: true },
  { id: id++, text: 'Вивчити Vue', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})
function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo">
    <button>Додати завдання</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(t)" :class='styleButton'>X</button>
    </li>
    <button @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Показати всі' : 'Сховати виконані' }}

    </button>
  </ul>
</template>


<style>
.done {
  text-decoration: line-through;
}
</style> -->

<!-- 9 Життєвий цикл і референції в шаблонах -->
<!-- 
<script setup>
import { ref, onMounted } from 'vue'

const pElementRef = ref(null)

onMounted(() => {
  pElementRef.value.textContent = 'Змонтовано!'
})

</script>

<template>
  <p ref="pElementRef">Привіт</p>
</template> -->


<!-- 10 спостерігачі -->
<!-- <script setup>
import { ref, watch } from 'vue'

const todoId = ref(1)
const todoData = ref(null)

async function fetchData() {
  todoData.value = null
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  todoData.value = await res.json()
}

fetchData()

watch(todoId, fetchData)
</script>

<template>
  <p>Завдання: {{todoId}}</p>
  <button @click="todoId++" :disabled="!todoData">Отримати наступне завдання</button>
  <p v-if="!todoData">Завантажується...</p>
  <pre v-else>{{ todoData }}</pre>
</template> -->

<!-- компоненти -->
<!-- <script setup>
import { ref } from 'vue';
import ChildComp from './components/ChildComp.vue'

const greeting = ref('Привіт від батьківського компонента!')
</script>

<template>
  <ChildComp :msg="greeting" />
</template> -->

<!-- випромінювання події батьківському компоненту -->
<script setup>
import { ref } from 'vue'
import ChildComp from './components/ChildComp.vue'

const childMsg = ref('Поки що немає повідомлення від дочірнього компонента')
</script>

<template>
  <ChildComp @response="(arg) => childMsg = arg" />
  <p>{{ childMsg }}</p>
</template>