<script setup>
import Header from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements/Index.vue';
import Action from './Action.vue';
import Graphic from './Resume/Graphic.vue';

import { computed } from 'vue'

/* Amount & label */
let amount = null;
let label = null;

/* Date */
let todayDate = new Date();
let day = ('0' + todayDate.getDate()).slice(-2);
let month = ('0' + (todayDate.getMonth() + 1)).slice(-2);
let year = todayDate.getFullYear();

let formattedDate = `${day}/${month}/${year}`;

/* movements */
let movements = [{
  id: 0,
  title: "Movimiento 1",
  description: "Lorem ipsum dolor sit amet",
  amount: 100,
  time: new Date("01-01-2024"),
}, {
  id: 1,
  title: "Movimiento 2",
  description: "Lorem ipsum dolor sit amet",
  amount: 200,
  time: new Date("01-01-2024"),
}, {
  id: 2,
  title: "Movimiento 3",
  description: "Lorem ipsum dolor sit amet",
  amount: 500,
  time: new Date("01-01-2024"),
}, {
  id: 3,
  title: "Movimiento 4",
  description: "Lorem ipsum dolor sit amet",
  amount: 200,
  time: new Date("01-01-2024"),
}, {
  id: 4,
  title: "Movimiento 5",
  description: "Lorem ipsum dolor sit amet",
  amount: -400,
  time: new Date("01-01-2024"),
}, {
  id: 5,
  title: "Movimiento 6",
  description: "Lorem ipsum dolor sit amet",
  amount: -600,
  time: new Date("01-01-2024"),
}, {
  id: 6,
  title: "Movimiento 7",
  description: "Lorem ipsum dolor sit amet",
  amount: -300,
  time: new Date("01-01-2024"),
}, {
  id: 7,
  title: "Movimiento 8",
  description: "Lorem ipsum dolor sit amet",
  amount: 0,
  time: new Date("01-01-2024"),
}, {
  id: 8,
  title: "Movimiento 9",
  description: "Lorem ipsum dolor sit amet",
  amount: 300,
  time: new Date("12-25-2023"),
}, {
  id: 9,
  title: "Movimiento 10",
  description: "Lorem ipsum dolor sit amet",
  amount: 500,
  time: new Date("12-25-2023"),
}];

const amounts = computed(() => {
  const lastDays = movements
    .filter(m => {
      const today = new Date();
      const oldDate = today.setDate(today.getDate() - 30);

      return m.time > oldDate;
    })
    .map(m => m.amount);

    return lastDays.map((m, i) => {
      const lastMovements = lastDays.slice(0, i);

      return lastMovements.reduce((sum, movement) => {
        return sum + movement;
      }, 0);
    });
})
</script>
<template>
  <Layout>
    <template #header>
      <Header/>
    </template>
    <template #resume>
      <Resume
        :label="label"
        :total-amount="1000000"
        :amount="amount"
        :date="formattedDate"
      >
        <template #graphic>
          <Graphic :amounts="amounts"/>
        </template>
        <template #action>
          <Action/>
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements
        :movements="movements"
      />
    </template>
  </Layout>
</template>