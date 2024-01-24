<script setup>
import Header from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements.vue';

let amount = null;
let label = null;

/* Date */
let todayDate = new Date();
let day = ('0' + todayDate.getDate()).slice(-2);
let month = ('0' + (todayDate.getMonth() + 1)).slice(-2);
let year = todayDate.getFullYear();

let formattedDate = `${day}/${month}/${year}`;
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
          graphic
        </template>
        <template #action>
          action
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements/>
    </template>
  </Layout>
</template>