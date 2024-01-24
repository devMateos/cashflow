<script setup>
defineProps({
  title: {
    type: String,
  }
});

</script>

<template>
  <div class="movement">{{ title }}</div>
</template>