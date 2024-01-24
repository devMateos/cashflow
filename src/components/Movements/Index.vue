<script setup>
import Movement from './Movement.vue';

defineProps({
  movements: {
    type: Array,
    default: () => [],
  }
});

</script>

<template>
  <div class="movements">
      <h2 class="title">Historial</h2>
      <div class="content">
          <Movement
              v-for="movement in movements"
              :key="movement.id"
              :title="movement.title"
          />
      </div>
  </div>
</template>

<style scoped>
.movements {
  max-height: 100%;
  padding: 0 8px;
  margin-bottom: 14px;
}

.title {
  margin: 8px 16px 24px 16px;
  color: var(--brand-blue);
}

.content {
  max-height: 68vh;
  display: flex;
  flex-direction: column;
  gap: 8px;
  overflow-y: scroll;
}
</style>