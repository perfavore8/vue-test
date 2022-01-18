<template>
<div class="data_row_wrapper">
    <div class="column">
        <labeled-input
            id="index"
            name="index"
            label="Индекс"
        />
        <labeled-input
            id="country"
            name="country"
            label="Страна"
        />
        <labeled-input
            id="region"
            name="region"
            label="Область"
        />
    </div>
    <div class="column">
        <!-- <div class="column"> -->
            <label for="city">Город</label>
            <input class="input" type="text" v-model="modelValue.city" name="city" id="city" :class="{ invalid: validationStatus.city.$error}">
            <small for='city' v-if="validationStatus.city.$error">* Обязательное поле</small>
        <labeled-input
            id="street"
            name="street"
            label="Улица"
        />
        <labeled-input
            id="house"
            name="house"
            label="Дом"
        />
  </div>
</div>
</template>

<script>
import LabeledInput from './InputField.vue';

export default {
    name: 'address-info',
    emits: ['update:modelValue'],
    props: ['modelValue', 'validationStatus'],
    components: {
        LabeledInput,
    },
}
</script>

<style>

</style>