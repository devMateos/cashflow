<script setup>
import Header from './Header.vue'
import Layout from './Layout.vue'
import Resume from './Resume/Index.vue'
import Movements from './Movements/Index.vue'
import Action from './Action.vue'
import Graphic from './Resume/Graphic.vue'

import { computed, onMounted, ref } from 'vue'

/* Amount & label */
let amount = ref(null)
let label = null

/* Date */
let todayDate = new Date()
let formattedDate = todayDate.toLocaleString('es-ES', {
  day: '2-digit',
  month: '2-digit',
  year: 'numeric'
})

let dateLabel = ref(formattedDate)
/* movements */
let movements = ref([])

const amounts = computed(() => {
  const lastDays = movements.value
    .filter((m) => {
      const today = new Date()
      const oldDate = today.setDate(today.getDate() - 30)

      return m.time > oldDate
    })
    .map((m) => m.amount)

  return lastDays.map((m, i) => {
    const lastMovements = lastDays.slice(0, i + 1)

    return lastMovements.reduce((sum, movement) => {
      return sum + movement
    }, 0)
  })
})

const totalAmount = computed(() => {
  return movements.value.reduce((sum, m) => {
    return sum + m.amount
  }, 0)
})

onMounted(() => {
  const movementsFromLocalStorage = JSON.parse(localStorage.getItem('movements'))

  if (Array.isArray(movementsFromLocalStorage)) {
    movements.value = movementsFromLocalStorage.map((m) => {
      return { ...m, time: new Date(m.time) }
    })
  }
})

function create(movement) {
  movements.value.push(movement)
  save()
}

function remove(id) {
  const index = movements.value.findIndex((m) => m.id === id)
  movements.value.splice(index, 1)
  save()
}

function save() {
  localStorage.setItem('movements', JSON.stringify(movements.value))
}

const select = (selectedAmount, index) => {
  amount.value = selectedAmount

  const dateString = movements.value[index].time.toLocaleString('es-ES', {
    day: '2-digit',
    month: '2-digit',
    year: 'numeric'
  })
  dateLabel.value = dateString
  console.log(amount.value, dateLabel.value)
}
</script>
<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume :label="label" :total-amount="totalAmount" :amount="amount" :date="dateLabel">
        <template #graphic>
          <Graphic :amounts="amounts" @select="select" />
        </template>
        <template #action>
          <Action @create="create" />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" @remove="remove" />
    </template>
  </Layout>
</template>
