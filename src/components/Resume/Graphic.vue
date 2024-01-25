<script setup>
import { computed } from 'vue'

const props = defineProps({
  amounts: {
    type: Array,
    default: () => [],
  }
});

const amountToPixels = (amount) => {
  const min = Math.min(...props.amounts);
  const max = Math.max(...props.amounts);
  return 200 - ((amount - min) / Math.abs(max - min)) * 200;
}

const zero = computed(() => {
  return amountToPixels(0);
})

const points = computed(() => {
  const total = props.amounts.length;
  return props.amounts.reduce((points, amount, i) => {
    const x = (300 / total) * (i + 1);
    const y = amountToPixels(amount);
    console.log(y);
    return `${points} ${x},${y}`;
  }, "0, 100")
  
  
})
</script>

<template>
  <div>
    <svg
      viewBox="0 0 300 200"
    >
      <line
        stroke="#c4c4c4"
        stroke-width="2"
        x1="0"
        :y1="zero"
        x2="300"
        :y2="zero"
      />
      <polyline
        fill="none"
        stroke="#0689B0"
        stroke-width="2"
        :points="points"
      />
      <line
        stroke="#04b500"
        stroke-width="2"
        x1="200"
        y1="0"
        x2="200"
        y2="200"
      />
    </svg>
    <p>Últimos 30 días</p>
  </div>
</template>

<style scoped>
svg {
  width: 100%;
}

p {
  text-align: center;
}
</style>