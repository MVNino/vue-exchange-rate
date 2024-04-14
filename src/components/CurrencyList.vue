<template>
    <div class="currency">
        <select :id="'select-' + defaultCurrency" v-model="currencySelected" @change="onSelectChanged">
            <option :key="currency.toLowerCase()" :value="currency" v-for="currency, index in currencies"
                :selected="currency === defaultCurrency">
                {{ currency }}</option>
        </select>
        <input type="number" :id="'input-' + defaultCurrency" v-model="amount" placeholder="0" @change="onAmountChanged" value="1" :readonly="isReadOnly" />
    </div>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits(['amountChanged', 'selectedCurrencyChanged'])

const props = defineProps({
    isReadOnly: {
        type: Boolean,
        required: true,
    },
    defaultCurrency: {
        type: String,
        required: true,
    }
})

const currencies = ref([
    "AED", "ARS", "AUD", "BGN", "BRL", "BSD", "CAD", "CHF", "CLP", "CNY",
    "COP", "CZK", "DKK", "DOP", "EGP", "EUR", "FJD", "GBP", "GTQ", "HKD",
    "HRK", "HUF", "IDR", "ILS", "INR", "ISK", "JPY", "KRW", "KZT", "MXN",
    "MYR", "NOK", "NZD", "PAB", "PEN", "PHP", "PKR", "PLN", "PYG", "RON",
    "RUB", "SAR", "SEK", "SGD", "THB", "TRY", "TWD", "UAH", "USD", "UYU",
    "VND", "ZAR"
])

// Currency
const currencySelected = ref(props.defaultCurrency)

const onSelectChanged = () => {
    emit('selectedCurrencyChanged', currencySelected)
}


// Amount
const amount = ref(0)

const onAmountChanged = () => {
    console.log('hey')
    emit('amountChanged', amount)
}
</script>