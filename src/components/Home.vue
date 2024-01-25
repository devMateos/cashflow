<script setup>
import Header from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements/Index.vue';
import Action from './Action.vue';
import Graphic from './Resume/Graphic.vue';

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
  amount: 1000,
}, {
  id: 1,
  title: "Movimiento 2",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}, {
  id: 2,
  title: "Movimiento 3",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}, {
  id: 3,
  title: "Movimiento 4",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}, {
  id: 4,
  title: "Movimiento 5",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}, {
  id: 5,
  title: "Movimiento 6",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}, {
  id: 6,
  title: "Movimiento 7",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}, {
  id: 7,
  title: "Movimiento 8",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}, {
  id: 8,
  title: "Movimiento 9",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}, {
  id: 9,
  title: "Movimiento 10",
  description: "Lorem ipsum dolor sit amet",
  amount: 1000,
}];

/* Amounts */
const amounts = [100, 200, 500, 200, -400, -600, -300, 0, 300, 500];

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