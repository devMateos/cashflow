<template>
  <Layout>
    <template #header>
      <Header></Header>
    </template>
    <template #resume>
      <Resume
      :label="'Ahorro total'"
      :total-amount="10000"
      :amount="amount"
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
  
<script setup>
import Header from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements/Index.vue';
import Action from './Action.vue';
import Graphic from './Resume/Graphic.vue';

let label = null;
let amount = null;
let movements = [
  {
    id: 0,
    title: 'Movimiento 1',
    description: 'Lorem ipsum dolor sit amet',
    amount: 1000,
  }, {
    id: 1,
    title: 'Movimiento 2',
    description: 'Lorem ipsum dolor sit amet',
    amount: 1000,
  }, {
    id: 2,
    title: 'Movimiento 3',
    description: 'Lorem ipsum dolor sit amet',
    amount: -1000,
  }, {
    id: 3,
    title: 'Movimiento 4',
    description: 'Lorem ipsum dolor sit amet',
    amount: 1000,
  }, {
    id: 4,
    title: 'Movimiento 5',
    description: 'Lorem ipsum dolor sit amet',
    amount: 1000,
  }, {
    id: 5,
    title: 'Movimiento 6',
    description: 'Lorem ipsum dolor sit amet',
    amount: -1000,
  }, {
    id: 6,
    title: 'Movimiento 7',
    description: 'Lorem ipsum dolor sit amet',
    amount: 1000,
  }, {
    id: 7,
    title: 'Movimiento 8',
    description: 'Lorem ipsum dolor sit amet',
    amount: 1000,
  }, {
    id: 8,
    title: 'Movimiento 9',
    description: 'Lorem ipsum dolor sit amet',
    amount: 1000,
  },
];

let amounts = [100, 200, 500, 200, -400, -600, -300, 0, 300, 500];

</script>
  