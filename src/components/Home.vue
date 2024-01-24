<script setup>
import Header from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements.vue';

</script>
<template>
  <Layout>
    <template #header>
      <Header/>
    </template>
    <template #resume>
      <Resume/>
    </template>
    <template #movements>
      <Movements/>
    </template>
  </Layout>
</template>