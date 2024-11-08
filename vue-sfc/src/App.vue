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
<!-- <script setup>
import { ref } from 'vue'
import ChildComp from './components/ChildComp.vue'

const childMsg = ref('Поки що немає повідомлення від дочірнього компонента')
</script>

<template>
  <ChildComp @response="(arg) => childMsg = arg" />
  <p>{{ childMsg }}</p>
</template> -->

<!-- Слоти -->
<!-- <script setup>
import { ref } from 'vue'
import ChildComp from './components/ChildComp.vue'

const msg = ref('з батьківського компонента')
</script>

<template>
  <ChildComp> Повідомлення:{{ msg }}</ChildComp>
</template> -->

<!--Цей приклад демонструє обробку введення користувача за допомогою директиви v-on.-->
<!-- <script setup>

import { ref } from 'vue'

const message = ref('Привіт світ!')

function reverseMessage() {
  // Доступ/зміна значення реквізиту через його властивість .value.
  message.value = message.value.split('').reverse().join('')
}

function notify() {
  alert('навігацію було припинено.')
}
</script>

<template>

  <h1>{{ message }}</h1>


  <button @click="reverseMessage">Повідомлення навиворіт</button>


  <button @click="message += '!'">Додати "!"</button>

  <a href="https://vuejs.org" @click.prevent="notify">
    Посилання з e.preventDefault()
  </a>
</template>

<style>
button,
a {
  display: block;
  margin-bottom: 1em;
}
</style> -->

<!--Тут ми прив'язуємо реактивно атрибути / властивості елемента до стану.Синтаксис :title є скороченням від v-bind:title.
-->
<!-- <script setup>
import { ref } from 'vue'

const message = ref('Привіт, світе!')
const isRed = ref(true)
const color = ref('green')

function toggleRed() {
  isRed.value = !isRed.value
}

function toggleColor() {
  color.value = color.value === 'green' ? 'blue' : 'green'
}
</script>

<template>
  <p>
    <span :title="message">
      Наведіть на мене вказівник миші на кілька секунд, щоб побачити мій
      динамічно пов'язаний заголовок!
    </span>
  </p>


  <p :class="{ red: isRed }" @click="toggleRed">
    Це має бути червоним... але натисніть мене, щоб перемкнути це.
  </p>

  
  <p :style="{ color }" @click="toggleColor">
    Це має бути зеленим і має перемикатися між зеленим і синім після
    натискання.
  </p>
</template>

<style>
.red {
  color: red;
  cursor: pointer;
}
</style> -->

<!--Ми можемо відтворювати вміст умовно або в циклі за допомогою директив v-if і v-for.-->
<!-- <script setup>
 
import { ref } from 'vue'

const show = ref(true)
const list = ref([1, 2, 3])
</script>

<template>
  <button @click="show = !show">Сховати/показати список</button>
  <button @click="list.push(list.length+1)">Додати число</button>
  <button @click="list.pop()">Забрати число</button>
  <button @click="list.reverse()">Зробити список зворотнім</button>

  <ul v-if="show && list.length">
    <li v-for="item of list">{{ item }}</li>
  </ul>
  <p v-else-if="list.length">Список не порожній, але прихований.</p>
  <p v-else>Список порожній.</p>
</template> -->

<!--Ми можемо створювати двосторонні зв'язки між вхідними даними стану та форми за допомогою директиви v-model.-->
<!-- <script setup>
import { ref } from 'vue'

const text = ref('Редагувати мене')
const checked = ref(true)
const checkedNames = ref(['Петро'])
const picked = ref('Один')
const selected = ref('А')
const multiSelected = ref(['А'])
</script>

<template>
  <h2>Введення тексту</h2>
  <input v-model="text"> {{ text }}

  <h2>Прапорець</h2>
  <input type="checkbox" id="checkbox" v-model="checked">
  <label for="checkbox">Відмічено: {{ checked }}</label>


  <h2>Прапорці декількох значень</h2>
  <input type="checkbox" id="petro" value="Петро" v-model="checkedNames">
  <label for="petro">Петро</label>
  <input type="checkbox" id="mary" value="Марічка" v-model="checkedNames">
  <label for="mary">Марічка</label>
  <input type="checkbox" id="iren" value="Ірина" v-model="checkedNames">
  <label for="iren">Ірина</label>
  <p>Відмічені імена:
  <pre>{{ checkedNames }}</pre>
  </p>

  <h2>Радіобокс</h2>
  <input type="radio" id="one" value="Один" v-model="picked">
  <label for="one">Один</label>
  <br>
  <input type="radio" id="two" value="Два" v-model="picked">
  <label for="two">Два</label>
  <br>
  <span>Обрано: {{ picked }}</span>

  <h2>Вибирання</h2>
  <select v-model="selected">
    <option disabled value="">Виберіть один, будь ласка</option>
    <option>А</option>
    <option>Б</option>
    <option>В</option>
  </select>
  <span>Обрано: {{ selected }}</span>

  <h2>Вибирання декількох значень</h2>
  <select v-model="multiSelected" multiple style="width:100px">
    <option>А</option>
    <option>Б</option>
    <option>В</option>
  </select>
  <span>Обрано: {{ multiSelected }}</span>
</template> -->

<!--
Тут ми показуємо найпростіший можливий компонент, який приймає реквізит і рендерить його.
Дізнайтеся більше про компоненти в посібнику!
-->
<!-- <script setup>
import { ref } from 'vue'
import ChildComp from './components/ChildComp.vue'

const itemsList = ref([
  { id: 0, text: 'Овочі' },
  { id: 1, text: 'Сир' },
  { id: 2, text: 'Щось інше, що їдять люди' }
])
</script>

<template>
  <ol>
    <ChildComp v-for="item in itemsList" :todo="item" :key="item.id"></ChildComp>
  </ol>
</template> -->

<!--
Простий редактор коду.
-->
<!-- <script setup>
import { marked } from 'marked'
import { debounce } from 'lodash-es'
import { ref, computed } from 'vue'

const input = ref('# привіт')

const output = computed(() => marked(input.value))

const update = debounce((e) => {
  input.value = e.target.value
}, 100)
</script>

<template>
  <div class="editor">
    <textarea class="input" :value="input" @input="update"></textarea>
    <div class="output" v-html="output"></div>
  </div>
</template>

<style>
body {
  margin: 0;
}

.editor {
  height: 100vh;
  display: flex;
}

.input,
.output {
  overflow: auto;
  width: 50%;
  height: 100%;
  box-sizing: border-box;
  padding: 0 20px;
}

.input {
  border: none;
  border-right: 1px solid #ccc;
  resize: none;
  outline: none;
  background-color: #f6f6f6;
  font-size: 14px;
  font-family: 'Monaco', courier, monospace;
  padding: 20px;
}

code {
  color: #f66;
}
</style> -->

<!--
Приклад створення багаторазового компонента таблиці та його використання із зовнішніми даними.
-->
<!-- <script setup>
import DemoGrid from './components/GridForm.vue'
import { ref } from 'vue'

const searchQuery = ref('')
const gridColumns = ['імя', 'сила']
const gridData = [
  { 'імя': 'Чак Норріс', 'сила': Infinity },
  { 'імя': 'Брюс Лі', 'сила': 9000 },
  { 'імя': 'Джекі Чан', 'сила': 7000 },
  { 'імя': 'Джет Лі', 'сила': 8000 }
]
</script>

<template>
  <form id="search">
    Пошук <input name="query" v-model="searchQuery">
  </form>
  <DemoGrid :data="gridData" :columns="gridColumns" :filter-key="searchQuery">
  </DemoGrid>
</template> -->

<!-- <script>
export default {
  data() {
    return {
      cost: 5,
      amount: 20,
    };
  },
  computed: {
    price: function () {
      return this.cost * this.amount;
    }
  },
  methods: {
    changeCost() {
      // Зміна значення cost, наприклад, на 1
      this.amount += 1; // Можете змінити логіку за потреби
    }
  }
}
</script>

<template>
  <button @click="changeCost">Змінити вартість</button>
  <p>Вартість: {{ cost }}</p>
  <p>кількість: {{ amount }}</p>
  <p>Ціна: {{ price }}</p>

</template> -->

<!-- 
<script setup>
import { ref } from 'vue'
let input = ref('привіт')

function inputFunc(event) {
  event.preventDefault();
  alert('це буде один раз')

}

</script>
<template>

  <a href="https://example.com" @click.once="inputFunc">{{ input }}</a>
</template> -->

<!-- <script setup>
import { ref } from 'vue';

let visible = ref(true);
let visible2 = ref(true);
let visible3 = ref(true);


function toggle() {
  visible.value = !visible.value; // Використовуємо .value для зміни значення ref
}
function toggle2() {
  visible2.value = !visible2.value; // Використовуємо .value для зміни значення ref
}
function toggle3() {
  visible3.value = !visible3.value; // Використовуємо .value для зміни значення ref
}
</script>

<template>
  <button @click="toggle">	{{ visible ? 'hide' : 'show' }}</button>
  <p v-if="visible">text</p>
  <button @click="toggle2">{{ visible2 ? 'hide' : 'show' }}</button>
  <p v-if="visible2">text2</p>
  <button @click="toggle3">{{ visible3 ? 'hide' : 'show' }}</button>
  <p v-if="visible3">text3</p></template> -->

<!-- <script setup>
import { computed } from 'vue';
let day = new Date
let days = ['ВС', 'ПН', 'ВТ', 'СР', 'ЧТ', 'ПТ', 'СБ'];
console.log(days[5]);
// Визначаємо назву поточного дня тижня
const currentDay = computed(() => days[day.getDay()]);
console.log(currentDay);
</script>

<template >
  <p v-if="currentDay === days[0]">Сегодня воскресенье</p>
  <p v-else-if="currentDay === days[1]">Сегодня понедельник</p>
  <p v-else-if="currentDay === days[2]">Сегодня вторник</p>
  <p v-else-if="currentDay === days[3]">Сегодня среда</p>
  <p v-else-if="currentDay === days[4]">Сегодня четверг</p>
  <p v-else-if="currentDay === days[5]">Сегодня пятница</p>
  <p v-else>Сегодня суббота</p>
</template> -->


<!-- <script setup>
import {  ref } from 'vue';

let old = ref(0)

console.log(old);


</script>

<template >
  <input type="number" v-model="old" placeholder="Введіть вік" />
  <p v-if='old < 18'>Дитя</p>
  <p v-else-if='old >=18 && old<=25'>Студент</p>
  <p v-else-if="old >= 26 && old <= 59 ">Військовозобов'язаний</p>
  <p v-else-if="old >= 60">Старий пеньок</p>

</template>  -->

<!-- <script setup>

import { ref } from 'vue';

let isAuth = ref(true);

function toggle() {
  isAuth.value=!isAuth.value
}

</script>

<template >

  <button @click="toggle">{{ isAuth ? 'hide' : 'show' }}</button>
  <p v-if="isAuth">+++</p>
  <p v-if="isAuth">+++</p>
    <p v-if="isAuth">+++</p>

</template> -->


<script setup>
import { ref } from 'vue'

const isVisibility = ref(true);
</script>
<template >

  <button @click="isVisibility = !isVisibility">Toggle visibility</button>
  <p v-show="isVisibility">Цей абзац може бути прихований або показаний.</p>

</template >

