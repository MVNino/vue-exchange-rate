<template>
  <Header />
  <p>Choose the currency and the amounts to get the exchange rate</p>

  <div class="container">
    <CurrencyList :isReadOnly=false :defaultCurrency="firstCurrency"
      @selectedCurrencyChanged="handleFirstCurrencySelected" @amountChanged="handleAmountChange" />

    <SwapCurrency :amountToConvert="+amountToConvert" :firstCurrency="firstCurrency" :secondCurrency="secondCurrency" />

    <CurrencyList :isReadOnly=true :defaultCurrency="secondCurrency"
      @selectedCurrencyChanged="handleSecondCurrencySelected" />
  </div>
</template>

<script setup>
import Header from "./components/Header.vue"
import CurrencyList from "./components/CurrencyList.vue"
import SwapCurrency from "./components/SwapCurrency.vue"
import { ref } from "vue";

const amountToConvert = ref(0)
const firstCurrency = ref('USD')
const secondCurrency = ref('EUR')

const handleAmountChange = (amount) => {
  amountToConvert.value = amount.value
}

const handleFirstCurrencySelected = (currencySelected) => {
  firstCurrency.value = currencySelected.value
}

const handleSecondCurrencySelected = (currencySelected) => {
  secondCurrency.value = currencySelected.value
}

</script>