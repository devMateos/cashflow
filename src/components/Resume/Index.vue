<template>
  <main>
    <p>{{ label }}</p>
    <h1>{{ amountCurrency }}</h1>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<script setup>
import { computed, defineProps } from 'vue';

const props = defineProps({
  label: {
    type: String,
  },
  totalAmount: {
    type: Number,
  },
  amount: {
    type: Number,
    default: null,
  }
});

const currencyFormatter = new Intl.NumberFormat('es-ES', {
  style: 'currency',
  currency: 'EUR',
})
const amountVisual = computed(() => {
  return props.amount != null ? props.amount : props.totalAmount;
});
const amountCurrency = computed(() => {
  return currencyFormatter.format(amountVisual.value);
});
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}
h1,
p {
  margin: 0;
  text-align: center;
}
h1 {
  margin-top: 14px;
  color: var(--brand-green);
}
.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>