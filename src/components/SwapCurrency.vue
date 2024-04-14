<template>
    <div class="swap-rate-container">
        <button class="btn" id="swap">
            Swap
        </button>
        <div class="rate" id="rate">{{ equivalentAmount }} --- {{ amountToConvert }}</div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    amountToConvert: {
        type: Number,
        required: true,
    },
    firstCurrency: {
        type: String,
        required: true,
    },
    secondCurrency: {
        type: String,
        required: true,
    }
})

const equivalentAmount = ref('')

fetch("https://open.exchangerate-api.com/v6/latest")
    .then(res => res.json())
    .then(data => {
        const rate = data.rates[props.secondCurrency] / data.rates[props.firstCurrency];
        equivalentAmount.value = `${props.amountToConvert} ${props.firstCurrency} = ${rate.toFixed(2)} ${props.secondCurrency}`;
        
        console.log('equiii : ', equivalentAmount.value)
        // amountEl_two.value = (amountEl_one.value * (rate)).toFixed(2);/
    });
</script>