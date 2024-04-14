<template>
  <Header />
  <p>Choose the currency and the amounts to get the exchange rate</p>

  <div class="container">
    <CurrencyList />

    <SwapCurrency />

    <CurrencyList />
  </div>
</template>

<script setup>
import Header from "./components/Header.vue"
import CurrencyList from "./components/CurrencyList.vue"
import SwapCurrency from "./components/SwapCurrency.vue"
</script>