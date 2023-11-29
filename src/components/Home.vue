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
        graphic
      </template>
      <template #action>
        action
      </template>
    </Resume>
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>
  
<script setup>
import Header from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements.vue';

let amount = null;
</script>
  
<style scoped></style>